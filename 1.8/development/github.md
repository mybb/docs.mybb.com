---
layout: page
title: GitHub Access
categories: ["development"]
---

<table id="toc" class="toc"><tr><td><div id="toctitle"><h2>Contents</h2></div>
<ul>
<li class="toclevel-1 tocsection-1"><a href="#Welcome"><span class="tocnumber">1</span> <span class="toctext">GitHub Access</span></a>
	<ul>
		<li class="toclevel-2 tocsection-2"><a href="#Basics"><span class="tocnumber">1.1</span> <span class="toctext">The Basics</span></a>
		<ul>
			<li class="toclevel-3 tocsection-3"><a href="#Beginners"><span class="tocnumber">1.1.1</span> <span class="toctext">Git/GitHub for Beginners</span></a></li>
			<li class="toclevel-3 tocsection-4"><a href="#Forking"><span class="tocnumber">1.1.2</span> <span class="toctext">Forking MyBB</span></a></li>
			<li class="toclevel-3 tocsection-5"><a href="#Configuration"><span class="tocnumber">1.1.3</span> <span class="toctext">Configuration</span></a></li>
			<li class="toclevel-3 tocsection-6"><a href="#Windows"><span class="tocnumber">1.1.4</span> <span class="toctext">Working on Windows</span></a></li>
		</ul>
		</li>
	</ul>
</li>
</ul>
</td></tr></table>
<h1> <span class="mw-headline" id="Welcome">GitHub Access</span></h1>
<p>Welcome to the Development GitHub Access page. This document describes how to access MyBB's projects and repositories hosted at GitHub and an example workflow for both Team Members and volunteers.</p>

<h2> <span class="mw-headline" id="Basics">The Basics</span></h2>
<p>While working with GitHub it is completely up to you as to what tools and software you use to help contribute to MyBB. If you're not confident with command line Git, GitHub provides and easy to use workspace with desktop software for Mac or Windows. This software helps you keep in sync with the development on all branches in the repository as well as your own projects. Where possible, we recommend using this software.</p>

<h3> <span class="mw-headline" id="Beginners">Git/GitHub For Beginners</span></h3>
<p>If you haven't worked with MyBB, Git or GitHub before we recommend following GitHub's <a href="https://help.github.com/categories/54/articles" title="GitHib Bootcamp">Bootcamp</a> which will get you started with contributing to projects. The MyBB Team are not here to help you with problems with Git or GitHub; we do expect you to have a technological understanding of this process.</p>

<h3> <span class="mw-headline" id="Forking">Forking MyBB</span></h3>
<p>Once you are setup with GitHub, visit the <a href="http://github.com/mybb" title="MyBB Project on GitHub">MyBB Project</a> on GitHub. MyBB 1.x is located within the <em>mybb</em> repository. Fork the repository; this creates your own copy for you to work on.</p>

<pre>	$ git clone git://github.com/mybb/mybb.git</pre>

<p>Our repository contains three main branches:</p>
<ul>
<li>
	<strong>Master</strong>
	<br /><em>Contains code that is publically released</em>
</li>
<li>
	<strong>Stable</strong>
	<br /><em>Contains security and other maintenance work on existing minor-point releases (1.6.x)</em>
</li>
<li>
	<strong>Feature</strong>
	<br /><em>Contains work on the next feature release or features that are to be implemented into a series (1.8.x)</em>
</ul>

<h3> <span class="mw-headline" id="Configuration">Configuration</span></h3>
<p>Before working on GitHub, be sure to add some important configuration data to your Git client.</p>

<ul>
	<li>
		<strong>Username</strong>
		<p>First, you need to tell Git your name so it can properly label the commits you make.</p>
		<pre>	$ git config --global user.name "John Doe"</pre>
	</li>
	<li>
		<strong>Email</strong>
		<p>Git saves your email address into the commits you make. GitHub uses the email address to associate your commits with your GitHub account.</p>
		<pre>	$ git config --global user.email "john@doe.com"</pre>
	</li>
</ul>

<p>For more information, please see GitHub's guide to <a href="https://help.github.com/articles/set-up-git" title="Setting up Git">setting up Git</a>.</p>

<h3> <span class="mw-headline" id="Windows">Working on Windows</span></h3>
<p>If you are working on a Windows environment you must ensure you commit all files with LF line endings. Please make sure you set the following options:</p>

<pre>	$ git config --global core.autocrlf false
	$ git config --global core.eol lf
</pre>

When reviewing a commit, if the entire file looks as though it has changed (and not just individual lines) then chances are the line endings are incorrect.
