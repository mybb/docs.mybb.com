---
layout: page
title:  "Permissions"
categories: [development]
---

MyBB relies on numerous settings, permissions, and quotas that can determine board functionality. These can be configured through:
- global board settings,
- individual forums' settings,
- individual users' permissions,
- global user groups' permissions,
- user groups' permissions for individual forums,
- visibility states of threads and posts.

While permissions checks related to specific actions (that result in data insertion or modification) are usually simple, resolving read access within the forum hierarchy may involve checking multiple unrelated entries (e.g. search results) and their parent hierarchy against multiple users' permissions (e.g. thread subscribers).

Missing or incorrect permission logic can compromise the board's integrity and confidentiality, and may be considered a [vulnerability](https://mybb.com/security).

## Permission Controls
### User Groups' Forum Permissions
Permissions of members of user groups in individual forums are stored in `mybb_forumpermissions` database table columns as `0` or `1`, with rows identified by:
- the group ID (`gid`), and
- the forum ID (`fid`).

Permissions related to read access include:
<table>
    <tr>
        <th>Name</th>
        <th><code>1</code> Meaning</th>
        <th>Conflict Resolution</th>
    </tr>
    <tr>
        <td><code>canview</code></td>
        <td>Can view forum (subforum list, rules, announcement list)</td>
        <td>if and only if any <code>1</code></td>
    </tr>
    <tr>
        <td><code>canviewthreads</code></td>
        <td>Can view threads and announcements</td>
        <td>if and only if any <code>1</code></td>
    </tr>
    <tr>
        <td><code>canonlyviewownthreads</code></td>
        <td>Cannot view threads created by other users or by guests</td>
        <td>if and only if <strong>all</strong> <code>1</code></td>
    </tr>
</table>

This data is cached in the `forumpermissions` [datacache](/1.8/development/datacache/).

### Moderators' Forum Permissions
Permissions related to forum moderation are stored in the `mybb_moderators` database table columns as `0` or `1`, with rows identified by:
- the user or group type (`isgroup`: `0` or `1`), and the ID of the user or the user group (`mid`), and
- the forum ID (`fid`).

Permissions related to read access include:
<table>
    <tr>
        <th>Name</th>
        <th><code>1</code> Meaning</th>
        <th>Conflict Resolution</th>
    </tr>
    <tr>
        <td><code>canviewdeleted</code></td>
        <td>Ability to view soft deleted content</td>
        <td>if and only if any <code>1</code></td>
    </tr>
    <tr>
        <td><code>canviewunapprove</code></td>
        <td>Ability to view unapproved content</td>
        <td>if and only if any <code>1</code></td>
    </tr>
    <tr>
        <td><code>canviewips</code></td>
        <td>Ability to view IP addresses</td>
        <td>if and only if any <code>1</code></td>
    </tr>
    <tr>
        <td><code>canviewmodlog</code></td>
        <td>Ability to view moderator logs</td>
        <td>if and only if any <code>1</code></td>
    </tr>
</table>

This data is cached in the `moderators` [datacache](/1.8/development/datacache/).

### Visibility State
A general visibility state of threads and posts is represented by a numeric value, stored in the `visible` column of the `mybb_threads` and `mybb_posts` database tables.

<table>
    <tr>
        <th>Value</th>
        <th>Meaning</th>
        <th>Access Conditions</th>
    </tr>
    <tr>
        <td><code>-2</code></td>
        <td>Draft</td>
        <td>the target user is the author, and is not a guest</td>
    </tr>
    <tr>
        <td><code>-1</code></td>
        <td>Soft Deleted</td>
        <td>
            For full access:
            <ul>
                <li>the target user has <code>canviewdeleted</code> moderator permission for containing forum</li>
            </ul>

            For deletion notice (without content):
            <ul>
                <li>the target user has <code>canviewdeletionnotice</code> permission for containing forum</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td><code>0</code></td>
        <td>Unapproved</td>
        <td>
            <ul>
                <li>the target user has <code>canviewunapprove</code> moderator permission for containing forum, or</li>
                <li>
                    <ul>
                        <li>the <code>showownunapproved</code> setting is enabled, and</li>
                        <li>the target user is the author, and is not a guest</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td><code>1</code></td>
        <td>Generally visible</td>
        <td></td>
    </tr>
</table>

Entries with the _draft_ code can usually be excluded, as drafts are managed separately (e.g. within the User CP).

### Forum Options
Certain forum options set in the Admin CP affect their visibility.

Options related to read access include:
<table>
    <tr>
        <th>Name</th>
        <th>Description</th>
        <th>Access Conditions</th>
    </tr>
    <tr>
        <td><i>Forum is Active?</i> (<code>active</code>)</td>
        <td>Whether a forum and its content is generally accessible</td>
        <td><code>1</code> for the forum and all parent forums</td>
    </tr>
    <tr>
        <td><i>Forum Password</i> (<code>password</code>)</td>
        <td>A global password required for access</td>
        <td>Password verified within the target user's session for the forum and all parent forums</td>
    </tr>
</table>

In addition to checking individual forums, their parent hierarchy may also need to be taken into account using:
- the `mybb_forums.pid` database table column, storing the parent forum's ID, and
- the `mybb_forums.parentlist` database table column, storing the IDs of all parent forums and the target forum.

This data is cached in the `forums` [datacache](/1.8/development/datacache/).

## Authorization Logic
### Forum Content Access
- **Forum Metadata**

  To view basic information of a forum (e.g. title, description), all of the following **must** be satisfied:
  - the forum and its parent forums are _active_ (`active` status is `1`)
  - the target user has viewing permissions for the forum and its parent forums (`canview` is `1`)

- **Forum Content**

  To view basic content associated with a forum (e.g. rules, announcement list), all of the following **must** be satisfied:
  - _Forum Metadata_ conditions are satisfied
  - the forum and its parent forums have no _password_ set, or the passwords were validated for the target user in their active session

- **Thread**

  To view a thread, all of the following **must** be satisfied:
  - _Forum Metadata_ conditions are satisfied for the associated forums
  - _Forum Content_ conditions are satisfied for the associated forums
  - the target user has thread viewing permissions for the forum (`canviewthreads` is `1`)
  - the target user has permissions to view anyone's threads for the forum (`canonlyviewownthreads` is `0`), or is the author of the thread and is not a guest
  - the thread's visibility conditions are satisfied for the target user (see [Visibility State](#visibility-state))

- **Post**

  To view a post, all of the following **must** be satisfied:
  - _Forum Metadata_ conditions are satisfied for the associated forums
  - _Forum Content_ conditions are satisfied for the associated forums
  - _Thread_ conditions are satisfied for the associated thread
  - the post's visibility conditions are satisfied for the target user (see [Visibility State](#visibility-state))

## Examples
_The following code is included for demonstrative purposes only, and may not conform to production coding standards._
  
- ### Fetching Recent Posts for the Current User

  ```php
  require_once MYBB_ROOT . 'inc/functions_search.php';
  
  $where = '';
  
  // forums that are not "active"
  if ($csv = get_inactive_forums()) {
      $where .= ' AND p.fid NOT IN (' . $csv . ')';
  }
  
  // forums with no "caview" permission for the current user,
  // forums with no "canviewthreads" permission for the current user,
  // forums with a password that was not verified for the current user
  if ($csv = get_unviewable_forums(true)) {
      $where .= ' AND p.fid NOT IN (' . $csv . ')';
  }
  
  // forums with "canonlyviewownthreads" condition for the current user
  $groupPermissions = forum_permissions();
  
  if ($groupPermissions === false) {
      throw new Exception('Forum permission cache problem');
  }
  
  $onlyOwnThreadsVisibleForums = [];
  
  foreach ($groupPermissions as $fid => $forum) {
      if (isset($forum['canonlyviewownthreads']) && $forum['canonlyviewownthreads'] == 1) {
          $onlyOwnThreadsVisibleForums[] = $fid;
      }
  }
  
  if ($onlyOwnThreadsVisibleForums) {
      if ($mybb->user['uid'] != 0) {
          $where .= ' AND (
              p.fid NOT IN (' . implode(',', $onlyOwnThreadsVisibleForums) . ') OR
              t.uid = ' . $mybb->user['uid'] . '
          )';
      } else {
          $where .= ' AND p.fid NOT IN (' . implode(',', $onlyOwnThreadsVisibleForums) . ')';
      }
  }
  
  // visibility state conditions for the posts and threads tables
  $where .= ' AND ' . get_visible_where('p');
  $where .= ' AND ' . get_visible_where('t');
  
  // execute query
  $query = $db->query("
      SELECT message
      FROM
          " . TABLE_PREFIX . "posts p
          LEFT JOIN " . TABLE_PREFIX . "threads t ON p.tid = t.tid
      WHERE 1=1 {$where}
      LIMIT 5
  ");
  ```
