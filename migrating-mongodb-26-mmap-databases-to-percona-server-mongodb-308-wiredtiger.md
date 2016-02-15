Migrating collections from a mongoDB 2.6 mmap database to Percona Server for mongoDB 3.0.8 wiredTiger

<!-- <div class="box-shadow"> -->
<a href="http://www.mongodb.org">
<img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/mongodb.png" width="200" height="200" align="right" style="margin-left: 24px" vspace="1px">
</a>


Last month I was tasked to upgrade our mongoDB infrastructure so first thing I did was to try to import a random dump to the new database - and it wasn't a straightforward process of couse, why should it be? :)

Luckily after some debugging and the help of the fellow sysadmins at the company I used to work we could finally resolve all the issues we faced; thereby I'm putting together this brief guide that hopefully will help you make the transition should you encounter any of the issues we had to deal with.
<br><br>

----

<br>
We hit three blockers on our way to restore the aforementioned dump made with MongoDB 2.6
<br>Our host was a __CentOS 7 VM__ (__KVM__) updated to Jan 11th, 2016:

<Ul>
<li>
The first blocker was an issue with the format of a JSON metadata file:

<blockquote>Failed: restore error: listDB.lists: error creating collection listDB.lists: error running create command: exception: specify size:<n> when capped is true</blockquote>

The solution was to simply __remove all references__ to __capped__ and __size__.

[Ioan Mircea](https://goo.gl/9eCBS0) deserves the credits as he was the one who pointed me in the right direction to start understanding what was happening there.

Juan Pablo Nogueira was kind enough to also share a one-liner to edit the files in place and fix the issue, which I reproduce below for your comfort:
<script src="https://gist.github.com/i90rr/647ea36211977d00a534.js"></script>
</li>

<li>
The second one has to be with a bug in mongoDB and the way it handles memory allocation:

<blockquote>"There's another issue that seems to be related with the cache of wiredTiger trying to use more memory than the available one (seems a common problem when running Mongo in containers of any kind like LXC/Docker/cgroups-kvm, etc.); it fails to accurately measure the free memory.</blockquote>

The solution to this issue was to manually allocate the minimum necessary memory for the cache using the __storage.wiredTiger.engineConfig.cacheSizeGB__ flag like this:
<script src="https://gist.github.com/i90rr/60d87d19fb29768548c2.js"></script>
Which leads us directly into the third issue :)
</li>

<li>
The final issue we faced was related to the _mongod daemon_ hanging indefinitely at random stages when restoring a collection: sometimes it hanged in an early stage of the restore process, some other times it froze well beyond half of it - [here is an screenshot](https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/mongodb_hung.png).
<br>While I couldn't find anything in the logs that lead me to think that this was a cache size issue I finally could get along with the restore process by setting __cacheSizeGB__ to a bigger value.
<blockquote>
In our tests I found that 2gb of RAM was enough for the cache size, however YMMV so you might need to play with this value until you find the correct one that works for you.
</blockquote>
</li>
</ul>

<br>
**Closure**
<br>
In the end we were able to successfully restore the needed dump.
<br>To avoid any possible conflicts the issued command was:
<ul><blockquote>mongorestore -v --maintainInsertionOrder --drop --stopOnError <i>DIRECTORY</i></blockquote></ul>

<br>
You might also find this related article useful:
<br>[The Ubuntu Incident - MongoDB: upgrade to the WiredTiger storage engine](https://ubuntuincident.wordpress.com/2016/02/07/mongodb-upgrade-to-the-wiredtiger-storage-engine/)

Tags: mongodb, percona, database, nosql, bigdata
