# MongoDB cheat sheet

## Releases

Version | Date | More
------- | ---- | ----
`4.4` | _June 09, 2020_ | [Annoucement](https://www.mongodb.com/blog/post/announcing-mongodb-44--mongodb-cloud), [Paper](https://webassets.mongodb.com/MongoDB_Whats_New_4.4.pdf)

## Client

### Command line

```bash
# start a new mongo server (daemon)
mongod --dbpath "C:\my\path" --port 27017

# start a mongo shell and be on mycollection
mongo --port 27017 mycollection

# restore from dump folder into mydbname database
mongorestore -d mydbname dump

# monitor basic usage statistics for each collection
mongotop

# monitor basic MongoDB server statistics
mongostat
```

Reference: [docs.mongodb.com/program/mongo](https://docs.mongodb.com/manual/reference/program/mongo)

### Mongo CLI

```javascript
// display current db
db
// display the existing collections on the db
show dbs
// get DB version
db.version()
// display help
db.help()
// get current operation
db.currentOp()
// display the existing collections on the db
show collections

// connect to db "training"
use training
// execute commands from a javascript file
load("my_file.js")
// display all entries in "movies" collection with a nice display
db.movies.find().pretty()
// remove one entry with its id
db.movies.remove({ "_id" : ObjectId("59e334a1a48ad3d58f40bb00") })
// display statistics on a collection
db.movieDetails.stat()
// rename a collection
db.cars.renameCollection("car")

// display startup log
use local
db.startup_log.find().pretty()

// exit the shell (or Ctrl+C)
quit()
```

### MongoDB Shell

[Introducing the new MongoDB Shell](https://www.mongodb.com/blog/post/introducing-the-new-shell) - June 8, 2020

## Tools

### Evergreen

[evergreen-ci/evergreen](https://github.com/evergreen-ci/evergreen), [evergreen.mongodb.com](https://evergreen.mongodb.com/waterfall/mongodb-mongo-master)

Articles:

- [Evergreen Continuous Integration: Why We Reinvented The Wheel](https://engineering.mongodb.com/post/evergreen-continuous-integration-why-we-reinvented-the-wheel/) - July 27, 2016
- [Testing Linearizability with Jepsen and Evergreen: “Call Me Continuously!”](https://engineering.mongodb.com/post/testing-linearizability-with-jepsen-and-evergreen-call-me-continuously/) - February 16, 2017
- [How We Test MongoDB: Evergreen](https://www.mongodb.com/presentations/how-we-test-mongodb-evergreen) - June 1, 2015

## Deployment typologies

- [FR - OVHcloud et MongoDB s’allient pour proposer une solution facilitant l’innovation des données dans le cloud](https://www.developpez.net/forums/d2109067/logiciels/solutions-d-entreprise/cloud-computing/ovhcloud-mongodb-s-allient-proposer-solution-facilitant-l-innovation-donnees-cloud/) - May 28, 2021
