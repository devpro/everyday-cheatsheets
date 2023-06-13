# Legacy mongo Shell

> The legacy mongo shell was deprecated in MongoDB 5.0 and removed in MongoDB 6.0 ([The MongoDB Shell versus the Legacy mongo Shell](https://www.mongodb.com/docs/mongodb-shell/#the-mdb-shell-versus-the-legacy-mongo-shell))

## Commands

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

## Additional commands

- Drop a database: `db.dropDatabase()`
- Create a collection: `db.createCollection("name", "options")`
- Delete a collection: `db.collection_name.drop()`
- Insert data: `db.collection_name.insert({...})`
- Update data: `db.collection_name.update({_id: ObjectId("...")}, {...})`
- Find data: `db.collection_name.find({...}).pretty()`
- Remove data: `db.collection_name.remove({...})`
