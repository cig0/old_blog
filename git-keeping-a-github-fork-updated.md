Git: keeping a GitHub fork updated

I keep returning to this life-saving post - a must when forking a project and creating pull requests - so I decided it is worth enough to have a _hard copy_ of it, just in case.

CC of [Keeping A GitHub Fork Updated by Dan Croak](https://robots.thoughtbot.com/keeping-a-github-fork-updated) below
<br><br>

----

<br>
I forked a GitHub repo _thoughtbot/dotfiles_ to _croaky/dotfiles_ and want to keep it updated.

**Track**

After I forked the repo to my GitHub account, I did this one time:

<ul>
git clone git@github.com:croaky/dotfiles.git
<br>cd dotfiles
<br>git remote add upstream git@github.com:thoughtbot/dotfiles.git
</ul>

<br>
**Update**

Each time I want to update, from my local master branch:

<ul>
git fetch upstream
<br>git rebase upstream/master
</ul>

The goal of the rebase is to have a cleaner history if I have local changes or commits on the repo. It’s the difference between the the left and the right in the image below:

<div style="margin: 0px auto; display: flex; justify-content: center;">
     <a href="http://gitready.com/advanced/2009/02/11/pull-with-rebase.html">
        <img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/pull-rebase-vs-pull.png" border="0" />
     </a>
</div>
<span style="margin: 0px auto; display: flex; justify-content: center; text-align: center; vertical-align: top; font-size: small;">Pull with rebase - click to open the full article</span>

**Commit rights upstream**

If I also have commit rights to the upstream repo, I can create a local upstream branch and do work that will go upstream there.

<ul>
git checkout -b upstream upstream/master
</ul>

Tags: git, cvs
