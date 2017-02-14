---
layout: post
title: Getting started with Git
subtitle: Initial commands to get started
tags: [git, basics, first, project]
---

In this article I will describe the process to set up your own git repository along with some basic commands to get started.

Before this..!! **What is git ??**

Git is basically a distributed version control software. In simple words, for example, say you are working on a project and with time you have come up with various improvements or versions of your project. Now, instead of maintaining copies (redundant) for each new feature or version, git allows you to maintain one repository in which you can switch between versions and keep track of features.

You can use web based service for git repository provided by [github](https://github.com/) and [bitbucket](https://bitbucket.org/). After you have created your account on any of these service, you need to [download](http://git-scm.com/downloads) git on you local computer.

So we are done setting up, lets use it.

<ul>
    <li><strong>Initializing a git repository</strong>: Open terminal or git bash from installed programs and type following commands<br clear="none" />
<pre class="lang:sh decode:true ">$ cd path/to/my/project
$ git init</pre>
Above command will make you current project directory a git repo.</li>
    <li><strong>Create repository on github: </strong>A very intuitive interface will let you create the repository online. If it's a fresh project you can copy(clone) this repo to your local using<br clear="none" /><br clear="none" />
    <pre class="lang:sh decode:true ">$ git clone https://github.com/someuser/someproject.git</pre>
    This will link you local repo to remote on github cloud. But if you have an existing project and want to link otherwise, then you need to add a source to local repo using
    <br clear="none" /><br clear="none" />
<pre class="lang:sh decode:true ">$ git remote add origin https://github.com/someuser/someproject.git</pre>
&nbsp;</li>
    <li>Run these command in your git bash, and you have successfully linked the project to online repository.</li>
    <li>You can make some changes and check its status by<br clear="none" /><br clear="none" />
<pre class="lang:sh decode:true ">$ git status</pre>
It will show all the new changes in your project</li>
    <li>Now you have to add these(or required) changes to your git by<br clear="none" /><br clear="none" />
<pre class="lang:sh decode:true ">$ git add .</pre>
This will add all the changes

or
<pre class="lang:sh decode:true ">$ git add &lt;myfile&gt;</pre>
This will add particular file with name <em>myfile</em>.</li>
    <li>After you have added your changes, you need to commit the changes. You can see your commit as one version of your project with whatever changes you have made. Every time you commit something it is maintained in git repository. Every commit has a commit id which is used to refer your version in future.<br clear="none" /><br clear="none" />
<pre class="lang:sh decode:true ">$ git commit -m 'this is my first commit'</pre>
Commit message is important as it's a brief description of your changes.</li>
    <li>Commit is a pointer to each version of your project, you can make as many commits as you want. So far all your changes are in local repository, to sync it with remote repo you need to push your commits using<br clear="none" /><br clear="none" />
<pre class="lang:sh decode:true ">$ git push origin master</pre>

<br clear="none" />So this is how you add changes in your project to online repository.<strong><br clear="none" /></strong></li>
</ul>
<div>You just learnt how to maintain your changes in project. Git is much more than this and is pretty useful is version control. More concepts include branches, sub modules and checking out to various version etc. You can find lot of tutorials online like <a title="this" href="https://www.atlassian.com/git/tutorials/" target="_blank" shape="rect">this</a> one or you can wait for an article from me in future :D </div>
<div></div>
<br clear="none" /><br clear="none" />