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
   If applicable, a Team member response to the author that their report has been acknowledged and is being processed.

3. ### Internal Processing
   1. #### Triage and Analysis
      The vulnerability is being assessed by team members handling security issues.

      A _[Vulnerability Report]_-prefixed staff-only thread is created in the **Development → 1.8** section.

      A _Low_ / _Medium_ / _High_ Risk is assigned and details related to causes, impact and possible solutions are attached.  The thread is added to the _Getting * Ready_ list for the upcoming version.

   2. #### Technical Assessment Feedback
   If applicable, a Team member informs the reporter whether their submission is confirmed, invalid, or no fix is expected.

   3. #### Remediation
      1. The development team and security team members prepare and implement measures (including code patches in `git diff` format, advisories and third party cooperation) that will eliminate or mitigate affected environments and prevent related threats in the future.

         Once an acceptable solution is provided, a `[fix]` link is added to the _Getting * Ready_ thread.

      2. Prepared countermeasures are verified internally.

   4. #### Consultation
   If applicable, Team members cooperate with the reporter to arrive with the best solution possible. During and after the solution development the patch details may be forwarded to the reporter to verify that all vulnerabilities have been properly addressed.

4. ### Releasing
   1. #### Package Verification
   Team members handling security issues verify that the release candidate QA packages contain valid countermeasures.

   2. #### Release
   The final QA packages are [published](/1.8/development/release-workflow/).

   3. #### Documentation
   The vulnerability information and attribution details are verified following the release.

5. ### Final Feedback
   If applicable, a team member responds to the original reporter providing status and details of the issue.
