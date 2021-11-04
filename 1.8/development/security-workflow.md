---
layout: page
title:  "Security Workflow"
categories: [development]
---

# Security Workflow

If the report is rejected at any point, the workflow skips to _Final Feedback_.

1. ### Reporting
   - Team members handling security issues and team leaders are required to have available and accessible public keys.
   - No initial reports should be transmitted over unencrypted or insecure channels.

2. ### Report Handling
   1. #### Confidentiality Assurance
   If the report is located in a publicly accessible location, a Team member attempts to soft delete it (if possible, e.g. on the Community Forums) or contact the author (or other party that might help removing it temporarily).

   2. #### Alerting Team Members
   A Team member alerts the Team (preferably on internal Discord `#staff-security` channel) and provides links and/or information.

   3. #### Acknowledgement
   If applicable, a Team member [responds](https://community.mybb.com/thread-219265.html) to the author that their report has been acknowledged and is being processed.

3. ### Internal Processing
   1. #### Triage and Analysis
      The vulnerability is assessed by team members handling security issues.

      A _[Vulnerability Report]_-prefixed staff-only thread is created for each valid vulnerability in the [Development → 1.8](https://community.mybb.com/forum-154.html) section, and added to the list of _Security issues_ in the appropriate _Getting 1.8.x Ready_ thread for an upcoming version.

      Information tracked in the opening post of the thread may include:
      - documentation:
        - a brief description (root cause, conditions, impact, vulnerability type),
        - a detailed analysis of the current codebase state and related code history,
        - links to drafts of related [security advisories](https://github.com/mybb/mybb/security/advisories),
        - possible solutions,
      - metadata:
        - severity (_Low_ / _Medium_ / _High_ Risk), basing on real-world impact,
        - a [CVSS score](https://www.first.org/cvss/calculator/3.1),
        - a [CWSS score](https://cwe.mitre.org/cwss/cwss_v1.0.1.html),
        - a [CVE ID](https://www.cve.org/) (applicable CNAs: MITRE Corporation; GitHub, Inc.),
        - relevant [CWE types](https://cwe.mitre.org/),
        - report origin, the reporter's details, and credit preferences.

   2. #### Technical Assessment Feedback
      If applicable, a Team member [responds](https://community.mybb.com/thread-219265.html) to the author and includes:
      - the triage status of each reported vulnerability (confirmed, invalid, or no fix is expected),
      - expected patch release timeline (usually the upcoming version),
      - a request for public attribution preferences and information (name and optional company/group affiliation).

   3. #### Remediation
      1. The development team and security team members prepare and implement measures (including code patches in `git diff` format and third party cooperation) that will eliminate or mitigate the vulnerabilities and prevent related threats in the future.

         Once an acceptable solution is provided, a `[fix]` link is added/updated in the _Getting 1.8.x Ready_ thread.

      2. Prepared patches are verified internally.

   4. #### Consultation
   If applicable, Team members cooperate with the reporter to arrive with the best solution possible. During and after the solution development the patch details may be forwarded to the reporter to verify that all vulnerabilities have been properly addressed.

   5. #### Documentation
      - ##### Release Metadata
       Information in the _Getting * Ready_ thread is updated, including _Additional values for version .md_ and the _Security issues_ and _Internal QA focus_ lists.

      - ##### Security Advisory Draft
      Drafts of [Security Advisories](https://github.com/mybb/mybb/security/advisories) for confirmed vulnerabilities are created:

        ```markdown
        ### Impact
        (...)

        [CVSS:3.1/...](https://www.first.org/cvss/calculator/...)

        ### Details
        (...)

        ### Patches
        MyBB 1.8.(...) resolves this issue with the following changes:

        - Commit: https://github.com/mybb/mybb/commit/
          - `.patch`: https://github.com/mybb/mybb/commit/.patch

        ### References
        - Release Notes: https://mybb.com/versions/1.8.(...)/

        ### For more information
        Go to [mybb.com/security](https://mybb.com/security/) to report possible security concerns or to learn more about security research at MyBB.

        ### Contact
        The security team can be reached at [security@mybb.com](mailto:security@mybb.com).
        ```

4. ### Releasing
   1. #### Package Verification
   Team members handling security issues verify that the release candidate QA packages contain valid patches.

   2. #### Release
   The final Release Candidate packages are [published](/1.8/development/release-workflow/) as official stable releases.

   3. #### Advisory Publication
      1. Relevant security advisories are published.
      2. If applicable, CVE update requests are submitted to relevant CNAs.

   4. #### Attribution Verification
   The vulnerability information and attribution credits are verified (Release Blog Post, Release Notes).

5. ### Final Feedback
   If applicable, a team member [responds](https://community.mybb.com/thread-219265.html) to the original reporter and includes:
   - version numbers of products containing related patches,
   - links to related publications with acknowledgements (Release Blog Post, Release Notes),
   - links to related security advisories,
   - related CVE IDs.
