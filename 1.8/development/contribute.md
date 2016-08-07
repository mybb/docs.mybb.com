---
layout: page
title:  "Contribute"
categories: [development]
---

MyBB is free, open-source software. Anyone can contribute to its development and progress. MyBB source code is hosted on GitHub, which makes it easy to contribute to the project.

## Getting Started

MyBB follows the [Gitflow Workflow](https://www.atlassian.com/git/workflows#!workflow-gitflow).

If you already know what you're doing, contributing to one of our repositories is easy:

1. Fork a repository
2. Make your changes
3. Push the changes to the forked repository
4. Send a pull request

## Git/GitHub For Beginners

If you haven't worked with Git or GitHub before we recommend learning about it from the following resources:

- [Official Git Documentation](https://git-scm.com/documentation)
- [GitHub Bootcamp](https://help.github.com/categories/54/articles)
- [Try Git: Code School](https://try.github.io)

The MyBB Team are not here to help you with problems with Git or GitHub. We expect you to have an understanding of this process if you are contributing.

While working with GitHub it is completely up to you as to what tools and software you use to help contribute to MyBB. If you're not confident with command line Git, GitHub provides an easy to use workspace with desktop software for Mac or Windows. This software helps you keep in sync with the development on all branches in the repository as well as your own projects. Where possible, we recommend using this software.

## Configuration

Before working on GitHub, be sure to add some important configuration data to your Git client.

### Username

First, you need to tell Git your name so it can properly label the commits you make.

    $ git config --global user.name "John Doe"

### Email

Git saves your email address into the commits you make. GitHub uses the email address to associate your commits with your GitHub account.

    $ git config --global user.email "john@doe.com"

For more information, please see [GitHub's guide on setting up Git](https://help.github.com/articles/set-up-git).

### Working on Windows

If you are working on a Windows environment you must ensure you commit all files with LF line endings. Please make sure you set the following options:

    $ git config --global core.autocrlf false
    $ git config --global core.eol lf

When reviewing a commit, if the entire file looks as though it has changed (and not just individual lines) then chances are the line endings are incorrect.

## Working with GitHub's Issue Tracker

While all team members are able to contribute directly with the repositories, SQA are still required to confirm the work fixes the issue/no issues arise from the feature. An issue therefore may have several labels/statuses throughout development

The basic status is **Open** or **Closed**. GitHub provides an easy to use UI to differentiate between these statuses with tabs at the top of the issue list. In the terminology, a *developer* may be a member of the Development Team, a member of the MyBB Group, or a 3rd party contributor who is not a member of either Team or Group. The *reporter* is the person(s) who originally reported the issue.

An **Open** issue describes a problem that is yet to be fixed by a developer. These may have the following labels:

<dl>
    <dt>s:confirmed</dt>
    <dd>The issue has been confirmed as being a valid problem with MyBB and contains enough evidence for a developer to work on a fix.</dd>

    <dt>s:feedback</dt>
    <dd>
        The issue may not contain enough evidence of a valid problem, or difficult to reproduce, and requires more input from the reporter.

        The issue may have been fixed by a developer but may not have actually solved the problem/causes further problems/contains code that doesn't match the Development Standards.
    </dd>

    <dt>s:in-progress</dt>
    <dd>The issue is being worked on by someone.</dd>

    <dt>s:deferred</dt>
    <dd>The issue should be fixed in the future, but is not a current priority and may or may not be fixed in the near future.</dd>

    <dt>p:immediate</dt>
    <dd>The issue demands an immediate fix because it affects all or nearly all MyBB users and may cause serious errors or functionality bugs that make the software difficult to use.</dd>

    <dt>p:urgent</dt>
    <dd>The issue is confirmed to affect many MyBB users and affects the software in a severe way, such as a security or data loss risk, or frequent server errors.</dd>

    <dt>p:high</dt>
    <dd>The issue is of high importance and necessitates a timely fix.</dd>

    <dt>p:normal</dt>
    <dd>The issue is of typical importance, neither more nor less important than the average report.</dd>

    <dt>p:low</dt>
    <dd>The issue is a minor bug that doesn't affect the function of MyBB often, or does so in a very minor way that is not significant.</dd>
</dl>

A **Closed** issue may have different labels depending on the outcome of the initial investigation:

<dl>
    <dt>s:fixed</dt>
    <dd>The issue has been fixed by a developer and the fix is confirmed as solving the problem by an SQA Team member.</dd>

    <dt>s:rejected</dt>
    <dd>
        The issue is a duplicate of an already reported issue
        The issue was not a valid issue with MyBB
        The issue is not reproducable (after Feedback attempts have been made)
        The issue is a feature request rather than a bug
    </dd>
</dl>
