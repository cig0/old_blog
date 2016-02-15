Migrating collections from a mongoDB 2.6 mmap database to Percona Server for mongoDB 3.0.8 wiredTiger

<!-- <div class="box-shadow"> -->
<a href="http://www.mongodb.org">
<img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/mongodb.png" width="200" height="200" align="right" style="margin-left: 24px" vspace="1px">
</a>


Last month I was tasked to upgrade our mongoDB infrastructure so first thing I did was try to import a random dump to the new database - and it wasn't a straightforward process of couse, why should it be? :)

Luckily after some debugging and the help of the fellow sysadmins at the company I used to work we could finally resolve all the issues we faced; thereby I'm putting together this brief guide that hopefully will help you make the transition should you encounter any of the issues we had to deal with.

__We hit three blockers on our way to restore the aforementioned dump made with the legacy MongoDB 2.6__. Our host was a __CentOS 7 VM__ (__KVM__) updated to Jan 11th, 2016.

a) The first blocker was an issue with the format of a JSON metadata file:

Failed: restore error: listDB.lists: error creating collection listDB.lists: error running create command: exception: specify size:<n> when capped is true

b) The second one has to be with a bug in MongoDB with the way it handles memory allocation, I quote:

"There's another issue that seems to be related with the cache of wiredTiger trying to use more memory than the available one (seems a common problem when running Mongo in containers of any kind like LXC/Docker/cgroups-kvm, etc.); it fails to accurately measure the free memory. [...]  I will implement the "storage.wiredTiger.engineConfig.cacheSizeGB" option to limit wiredTiger's cache size [...]"

c) The final issue we faced was related to the mongod daemon hanging indefinitely at random stages when restoring a collection: some times it hanged in an early stage of the restore process, some other times it froze well beyond half of the restore process (please check attached screenshot).

mongod_hung.png
Workaround

a) Remove all references to capped and size:
<script src="https://gist.github.com/i90rr/647ea36211977d00a534.js"></script>

b) Manually allocate the necessary memory for the cache using the storage.wiredTiger.engineConfig.cacheSizeGB flag like this:
<script src="https://gist.github.com/i90rr/60d87d19fb29768548c2.js"></script>

c) In our tests we found that 2GB was an appropriate value for the cache, however YMMV so you might need to play with the cache size until you find the correct value that works for you.
Resolution
<br>
We were able to successfully restore the needed dump. To avoid any possible conflicts the issued command was:
<blockquote># mongorestore -v --maintainInsertionOrder --drop --stopOnError DIRECTORY/</blockquote>




please [follow this link](https://www.percona.com/forums/questions-discussions/percona-server-for-mongodb/43561-mongorestore-hangs-restoring-a-mongodb-2-6-dump-to-a-ps-for-mongodb-3-0-8-wiredtiger "Mongorestore hangs restoring a MongoDB 2.6 dump to a PS for MongoDB 3.0.8 wiredTiger") for a quick explanation of the problems encountered and how to solve them, I will update this post next week with a hand-holding step-by-step guide.

Tags: mongodb, percona, database, nosql, bigdata
