Migrating mongoDB 2.6 mmap databases to {Percona Server} mongoDB 3.0.8 wiredTiger

<!-- <div class="box-shadow"> -->
<a href="http://www.mongodb.org">
<img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/mongodb.png" width="250" height="250" align="right" style="margin-left: 17px" vspace="8px">
</a>


Last month I was tasked to upgrade our mongoDB infrastructure so first thing I did was to try to import a random dump to the new database.
<br><br>
There was when the problems started...
<br><br>
Luckily after a lot of trial and error I could finally resolve all the issues I faced; please [follow this link](https://www.percona.com/forums/questions-discussions/percona-server-for-mongodb/43561-mongorestore-hangs-restoring-a-mongodb-2-6-dump-to-a-ps-for-mongodb-3-0-8-wiredtiger "Mongorestore hangs restoring a MongoDB 2.6 dump to a PS for MongoDB 3.0.8 wiredTiger") for a quick explanation of the problems encountered and how to solve them, I will update this post next week with a hand-holding step-by-step guide.

Tags: mongodb, percona, database, nosql, bigdata
