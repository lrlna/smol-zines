# MongoDB Basics


mmap used to be the default storage for mongodb, here is how it works:
![mmap](/guides/img/mongodb/mmap.jpg)

there is a mistake in this one, as of `MongoDB 3.0` WiredTiger is now the default!
more info in [zee docs](https://docs.mongodb.com/manual/core/wiredtiger/)
![wired-tiger](/guides/img/mongodb/wired-tiger.jpg)

a lil bit on replication! find out more from [the docs](https://docs.mongodb.com/manual/replication/)

![replication](/guides/img/mongodb/replicaiton.jpg)
![replication-failover](/guides/img/mongodb/replicaiton-failover.jpg)

and a bit more on sharding. as usual, more in [those docs](https://docs.mongodb.com/manual/sharding/)
![sharding](/guides/img/mongodb/sharding.jpg)

---
Not entirely related to MongoDB, but a good reading on architecting your applications is this book: [Designing Data-Driven Applications](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321). It's *ultra* good!
