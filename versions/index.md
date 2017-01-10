---
layout: page
title:  "Versions"
categories: [versions]
---

# Versions

On this page you will find a description of the MyBB versioning scheme and the release cycle.  Finally, there is a list of all MyBB versions released (beta and public).

## Version system

Starting from version 1.2.0, MyBB has used a 3-number versioning system, x.y.z, where x is the major version number, y is the minor version number, and z is the bug fix number.

The major version number is incremented when there is a major change in MyBB, such as a major rewrite of the core.

The minor version number indicates two things. Even numbers (ie. 2, 4, 6, etc) indicate public releases. Odd numbers (ie. 1, 3, 5, etc) indicate that the version is a development (non-public) version.

The bug fix version is incremented every time a security or maintenance update is released. These patches usually will not contain new major features, but are usually crucial to the security or functionality of your forum.

The version numbers above may overflow from one digit into two digits. For example, after 1.6.9, the next maintenance/security release would be 1.6.10.

Whatever the version number is, MyBB always urges users to upgrade to the latest version for the highest security of MyBB installations. Even minor patches that seem insignificant can protect from possibly critical security vulnerabilities.

## Release cycle

### Major releases

Major releases increment the major or minor version number (see version system above). Usually these will have new features and changes to the database schema, and therefore may break existing forum customizations, such as themes and plugins. Major releases may also contain security vulnerability patches and bug fixes.
Major releases usually end with a 0 (zero) in the version number (eg. x.y.0 or x.0.0) and usually mark the start of a new **series**.
MyBB's major releases thus far include 1.00, 1.2.0, 1.4.0 and 1.6.0.

### Minor releases

Minor releases are produced as necessary in between major releases. They fall into two categories, but may be combined in a release. Customizations (plugins, themes, etc.) generally are compatible across releases in one series.

#### Security Vulnerability Patches

These are released as often as necessary to fix any known security holes. Upgrading should be completed as soon as possible, or forum security could be compromised.

#### Bug Fix / Maintenance Releases

These fix bugs and small errors in the software. Upgrading is not as immediately necessary with simple maintenance releases as it is with security vulnerability patches, but it is recommended and encouraged to upgrade as soon as it is convenient.

## Version List

The following is a list of official (public and private) releases of MyBB from the MyBB Group.

Download links are provided on this page for older versions for non-production-site usage (i.e. porting old modifications, converting to MyBB, looking at what MyBB was back then, etc).

**Official support is *not* provided for these old versions, and if you choose to use them, you do so at your own risk - most of the old versions have known bugs or exploits.  The MyBB Group encourages that all administrators use the latest version of MyBB for production sites.**

### Version 2 series

#### *2.0.x*

[2.0.0](2.0.0) *`In planning`*

### Version 1 series

#### 1.8.x

| Version Number | Release Date | Release type | Availability |
| :------------: | ------------ | ------------ | :---------: |
| [1.8.10](1.8.10) *`Latest`* | 10 January 2017 | Maintenance Release | [Download](https://resources.mybb.com/downloads/mybb_1810.zip) |
| [1.8.9](1.8.9) | 21 December 2016 | Security and Maintenance Release | [Download](https://resources.mybb.com/downloads/mybb_1809.zip) |
| [1.8.8](1.8.8) | 17 October 2016 | Security and Maintenance Release | [Download](https://resources.mybb.com/downloads/mybb_1808.zip) |
| [1.8.7](1.8.7) | 11 March 2016 | Security and Maintenance Release | [Download](https://resources.mybb.com/downloads/mybb_1807.zip) |
| [1.8.6](1.8.6) | 7 September 2015 | Security and Maintenance Release | [Download](https://resources.mybb.com/downloads/mybb_1806.zip) |
| [1.8.5](1.8.5) | 27 May 2015 | Security and Maintenance Release | [Download](https://resources.mybb.com/downloads/mybb_1805.zip) |
| [1.8.4](1.8.4) | 15 February 2015 | Feature Update, Security and Maintenance Release | [Download](https://resources.mybb.com/downloads/mybb_1804.zip) |
| [1.8.3](1.8.3) | 20 November 2014 | Security Release | [Download](https://resources.mybb.com/downloads/mybb_1803.zip) |
| [1.8.2](1.8.2) | 13 November 2014 | Security Release | [Download](https://resources.mybb.com/downloads/mybb_1802.zip) |
| [1.8.1](1.8.1) | 23 October 2014 | Maintenance Release | [Download](https://resources.mybb.com/downloads/mybb_1801.zip) |
| [1.8.0](1.8.0) | 1 September 2014 | Major Release | [Download](https://resources.mybb.com/downloads/mybb_1800.zip) |

#### 1.6.x

| Version Number | Release Date | Release type | Availability |
| :------------: | ------------ | ------------ | :---------: |
| [1.6.18](1.6.18) | 7 September 2015 | Security Release | [Download](https://resources.mybb.com/downloads/mybb_1618.zip) |
| [1.6.17](1.6.17) | 27 May 2015 | Security Release | [Download](https://resources.mybb.com/downloads/mybb_1617.zip) |
| [1.6.16](1.6.16) | 20 November 2014 | Security Release | [Download](https://resources.mybb.com/downloads/mybb_1616.zip) |
| [1.6.15](1.6.15) | 4 August 2014 | Maintenance and Security Release | [Download](https://resources.mybb.com/downloads/mybb_1615.zip) |
| [1.6.14](1.6.14) | 30 June 2014 | Maintenance and Security Release | [Download](https://resources.mybb.com/downloads/mybb_1614.zip) |
| [1.6.13](1.6.13) | 26 April 2014 | Maintenance and Security Release | [Download](https://resources.mybb.com/downloads/mybb_1613.zip) |
| [1.6.12](1.6.12) | 30 December 2013 | Maintenance and Security Release | [Download](https://resources.mybb.com/downloads/mybb_1612.zip) |
| [1.6.11](1.6.11) | 8 October 2013 | Maintenance and Security Release | [Download](https://resources.mybb.com/downloads/mybb_1611.zip) |
| [1.6.10](1.6.10) | 22 April 2013 | Maintenance and Security Release | [Download](https://resources.mybb.com/downloads/mybb_1610.zip) |
| [1.6.9](169) | 15 December 2012 | Security Release | [Download](https://resources.mybb.com/downloads/mybb_1609.zip) |
| [1.6.8](https://blog.mybb.com/2012/05/27/mybb-1-6-8-released-maintenance-release/) | 27 May 2012 | Maintenance Release |  -  |
| [1.6.7](https://blog.mybb.com/2012/04/01/mybb-1-6-7-update-1-8-development/) | 1 April 2012 | Feature Update, Security and Maintenance Release |  - |
| [1.6.6](https://blog.mybb.com/2012/02/10/mybb-1-6-6-security-release/) | 10 February 2012 | Security Release |  -  |
| [1.6.5](https://blog.mybb.com/2011/11/25/mybb-1-6-5-released-feature-update-security-maintenance-release/) | 25 November 2011 | Feature Update, Security and Maintenance Release |  -  |
| [1.6.4](https://blog.mybb.com/2011/07/26/mybb-1-6-4-released-feature-update-security-maintenance-release/) | 26 July 2011 | Feature Update, Security and Maintenance Release |  -  |
| [1.6.3](https://blog.mybb.com/2011/04/17/mybb-1-6-3-and-1-4-16-security-update/) | 17 April 2011 | Security Release |  -  |
| [1.6.2](https://blog.mybb.com/2011/02/22/mybb-1-6-2-and-1-4-15-security-update/) | 22 February 2011 | Security and Maintenance Release |  -  |
| [1.6.1](https://blog.mybb.com/2010/12/15/mybb-1-6-1-release-1-4-14-update/) | 15 December 2010 | Security and Maintenance Release |  -  |
| [1.6.0](https://blog.mybb.com/2010/08/03/mybb-1-6-released/) | 3 August 2010 | Major Release |  -  |

#### 1.4.x

| Version Number | Release Date | Release type | Availability |
| :------------: | ------------ | ------------ | :---------: |
| [1.4.16](https://blog.mybb.com/2011/04/17/mybb-1-6-3-and-1-4-16-security-update/) | 17 April 2011 | Security release |  -  |
| [1.4.15](https://blog.mybb.com/2011/02/22/mybb-1-6-2-and-1-4-15-security-update/) | 22 February 2011 | Maintenance release |  -  |
| [1.4.14](https://blog.mybb.com/2010/12/15/mybb-1-6-1-release-1-4-14-update/) | 2 August 2010 | Maintenance release |  -  |
| [1.4.13](https://blog.mybb.com/2010/04/19/mybb-1-4-13-released-security-patches-to-mybb-1-4-12/) | 19 April 2010 | Security patch release |  -  |
| [1.4.12](https://blog.mybb.com/2010/04/13/mybb-1-4-12-released-security-maintenance-update/) | 13 April 2010 | Security and Maintenance release |  -  |
| [1.4.11](https://blog.mybb.com/2009/12/29/mybb-1-4-11-released-minor-patch-security-update/) | 29 December 2009 | Minor patch and security release |  -  |
| [1.4.10](https://blog.mybb.com/2009/12/01/mybb-1-4-10-released-maintenance-release/) | 1 December 2009 | Maintenance release |  -  |
| [1.4.9](https://blog.mybb.com/2009/09/21/mybb-1-4-9-released-security-update/) | 21 September 2009 | Security release |  -  |
| [1.4.8](https://community.mybb.com/thread-51952.html) | 26 June 2009 | Security and Maintenance release |  -  |
| [1.4.7](https://community.mybb.com/thread-51349.html) | 15 June 2009 | Security release |  -  |
| [1.4.6](https://community.mybb.com/thread-49231.html) | 3 May 2009 | Security release |  -  |
| [1.4.5](https://community.mybb.com/thread-48484.html) | 19 April 2009 | Security and Maintenance release |  -  |
| [1.4.4](https://community.mybb.com/thread-41036.html) | 27 November 2008 | Security and Maintenance release |  -  |
| [1.4.3](https://community.mybb.com/thread-39705.html) | 29 October 2008 | Security vulnerability patch |  -  |
| [1.4.2](https://community.mybb.com/thread-37792.html) | 17 September 2008 | Security and Maintenance release |  -  |
| [1.4.1](https://community.mybb.com/thread-36022.html) | 17 August 2008 | Security and Maintenance release |  -  |
| [1.4.0](https://community.mybb.com/thread-34565.html) | 3 August 2008 | Major Release  |  -  |

#### 1.2.x

| Version Number | Release Date | Release type | Availability |
| :------------: | ------------ | ------------ | :---------: |
| [1.2.14](https://community.mybb.com/thread-33865.html) | 18 July 2008 | Security and Maintenance release |  -  |
| [1.2.13](https://community.mybb.com/thread-31666.html) | 21 May 2008 | Security vulnerability patch |  -  |
| [1.2.12](https://community.mybb.com/thread-27675.html) | 20 January 2008 | Security and Maintenance release |  -  |
| [1.2.11](https://community.mybb.com/thread-27227.html) | 8 January 2008 | Security vulnerability patch |  -  |
| [1.2.10](https://community.mybb.com/thread-26083.html) | 1 December 2007 | Maintenance Release |  -  |
| [1.2.9](https://community.mybb.com/thread-20910.html) | 10 July 2007 | Security vulnerability patch |  -  |
| [1.2.8](https://community.mybb.com/thread-20463.html) | 28 June 2007 | Maintenance and Security vulnerability patch |  -  |
| [1.2.7](https://community.mybb.com/thread-19241.html) | 15 May 2007 | Maintenance and Security vulnerability patch |  -  |
| [1.2.6](https://community.mybb.com/thread-18632.html) | 25 April 2007 | Security vulnerability patch |  -  |
| [1.2.5](https://community.mybb.com/thread-18301.html) | 13 April 2007 | Security vulnerability patch |  -  |
| [1.2.4](https://community.mybb.com/thread-18002.html) | 4 April 2007 | Security vulnerability patch |  -  |
| [1.2.3](https://community.mybb.com/thread-16273.html) | 14 February 2007 | Maintenance and Security vulnerability patch |  -  |
| [1.2.2](https://community.mybb.com/thread-14181.html) | 1 December 2006 | Maintenance and Security vulnerability patch |  -  |
| [1.2.1](https://community.mybb.com/thread-14090.html) | 26 November 2006 | Small security update.  Version number unchanged. |  -  |
| [1.2.1](https://community.mybb.com/thread-12705.html) | 27 September 2006 | Maintenance and Security vulnerability patch |  -  |
| [1.2.0](https://community.mybb.com/thread-11781.html) | 2 September 2006 | Major Release |  -  |

#### 1.1.x and 1.0x

| Version Number | Release Date | Release type | Availability |
| :------------: | ------------ | ------------ | :---------: |
| [1.1.8](https://community.mybb.com/thread-11697.html) | 30 August 2006 | Security vulnerability patch |  -  |
| [1.1.7](https://community.mybb.com/thread-10853.html) | 27 July 2006 | Security vulnerability patch |  -  |
| [1.1.6](https://community.mybb.com/thread-10555.html) | 25 July 2006 | Security vulnerability patch |  -  |
| [1.1.5](https://community.mybb.com/thread-10115.html) | 27 June 2006 | Security vulnerability patch |  -  |
| [1.1.4](https://community.mybb.com/thread-9955.html) | 22 June 2006 | Security vulnerability patch |  -  |
| [1.1.3](https://community.mybb.com/thread-9622.html) | 10 June 2006 | Security vulnerability patch |  -  |
| [1.1.2](https://community.mybb.com/thread-8733.html) | 6 May 2006 | Security vulnerability patch |  -  |
| [1.1.1](https://community.mybb.com/thread-8232.html) | 14 April 2006 | Security vulnerability patch |  -  |
| [1.1.0](https://community.mybb.com/thread-7368.html) | 8 March 2006 | Also known as 1.1 or 1.10 - Security and bug fixes |  -  |
| [1.0.4](https://community.mybb.com/thread-6777.html) | 15 February 2006 | Security vulnerability patch |  -  |
| [1.0.3](https://community.mybb.com/thread-6418.html) | 31 January 2006 | Security vulnerability patch |  -  |
| [1.0.2](https://community.mybb.com/thread-5852.html) | 11 January 2006 | Security vulnerability patch (Originally released on 7 January 2006) |  -  |
| [1.0.1](https://community.mybb.com/thread-5633.html) | 28 December 2005 | Security vulnerability patch |  -  |
| [1.0.0](https://community.mybb.com/thread-5184.html) | 9 December 2005 | Major release | - |

#### Preview Releases

| Version Number | Release Date | Release type | Availability |
| :------------: | ------------ | ------------ | :---------: |
| [PR2](https://community.mybb.com/thread-4507.html) `Sec.Update` | 1 November 2005 | Security vulnerability patch |  -  |
| [PR2](https://community.mybb.com/thread-3633.html) `Rev.686` | 3 September 2005 | Maintenance release | - |
| [PR2](https://community.mybb.com/thread-3528.html) | 30 August 2005 | Major release (presented major improvements since RC4) | - |
| [PR1](pr-1) | March 2005 | Private beta release | - |

#### Pre-1.0 (Release Candidate/Beta) series

| Version Number | Release Date | Release type | Availability |
| :------------: | ------------ | ------------ | :---------: |
| [RC4](rc4) | 4 October 2004 | (Release Candidate 4) | - |
| [RC3](rc3) | 10 July 2004 | (Release Candidate 3) | - |
| [RC2](rc2) | 22 February 2004 | (Release Candidate 2) | - |
| [RC1](rc1) | 10 December 2003 | (Release Candidate 1) | - |
| [Beta 4](beta-4) | August 2003 | Beta release | - |
| [DevBB](devbb) | Pre-2003 | Predecessor to MyBB | - |
