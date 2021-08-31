# MongoDB

> MongoDB is a general purpose, document-based, distributed database built for modern application developers and for the cloud era.

→ [mongodb.com](https://www.mongodb.com/), [Github](https://github.com/mongodb), [Twitter](https://twitter.com/MongoDB), [developer.mongodb.com](https://developer.mongodb.com)

## Learn

### Official resources

* [Documentation](https://docs.mongodb.com/)
* [Resources](https://www.mongodb.com/resources): presentations, webinars, white papers
* [MongoDB University](https://university.mongodb.com/)

### Products

* [Atlas](./atlas.md)
* [Compass](./compass.md)
* [Evergreen](./evergreen.md)
* [Ops Manager](./mongodb-opsmanager.md)

### News

* [Events](./mongodb-events.md)

## Releases

Version | Date | More
------- | ---- | ----
`4.4` | _June 09, 2020_ | [Annoucement](https://www.mongodb.com/blog/post/announcing-mongodb-44--mongodb-cloud), [Paper](https://webassets.mongodb.com/MongoDB_Whats_New_4.4.pdf)
[`4.2`](./mongodb-42.md) | |

## First steps

### MongoDB Shell

Go to the [download center](https://www.mongodb.com/download-center), select "Server", then "MongoDB Community Server" edition, chose the target platform and version and let the download complete.

#### MongoDB Shell on Windows

* You'll download a file like `mongodb-win32-x86_64-2008plus-ssl-4.0.4.zip`
* Unzip the content of the archive in a program folder (for example `D:\Programs` folder)
* Rename the folder with something explicit like `mongodb-community-4.0.4`
* You can either update your PATH globally on your machine or do it when you need it (or through a bat file)

  ```dos
  SET PATH=%PATH%;D:\Programs\mongodb-community-4.0.4\bin
  ```

#### First commands

* The following command must return a valid output

  ```dos
  mongo --version
  ```

  > MongoDB shell version v4.0.4  
  > git version: f288a3bdf201007f3693c58e140056adf8b04839  
  > allocator: tcmalloc  
  > modules: none  
  > build environment:  
  > distmod: 2008plus-ssl  
  > distarch: x86_64  
  > target_arch: x86_64  

### Local Server

* If you followed the steps to have the Mongo Shell, you'll be able to launch easily a MongoDB server locally (`mongod`).

  ```bash
  # make sure the data path exists
  md /path/to/data
  # start a basic MongoDB instance (default port 27017)
  mongod --dbpath=/path/to/data
  ```

* You can then connect with the MongoDB Shell:

  ```bash
  mongo
  ```

### Docker

* Check the images already downloaded locally

  ```bash
  docker images
  ```

* Get the image for a specific version of MongoDB

  ```bash
  docker image pull mongo:4.0.4
  ```

* Start the container

  ```bash
  docker run -d -p 27017:27017 --name mongodb404 mongo:4.0.4
  ```

## Server

### Start with Docker

```bash
docker run --name mongodb -d -p 27017:27017 mongo:4.4.6
```

### Start from the command line

```bash
mongod --dbpath "C:\my\path" --port 27017
```

## Client

### Command line

```bash
# start a mongo shell and be on mycollection
mongo --port 27017 mycollection

# restore from dump folder into mydbname database
mongorestore -d mydbname dump

# monitor basic usage statistics for each collection
mongotop

# monitor basic MongoDB server statistics
mongostat
```

→ [docs.mongodb.com/program/mongo](https://docs.mongodb.com/manual/reference/program/mongo)

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

### MongoDB Shell (mongosh)

Introduced in June 2020, avalable as a standalone package, it provides a fully functional JavaScript/Node.js environment for interacting with MongoDB deployments. It can be used to test queries and operations directly with one database.

→ [Documentation](https://docs.mongodb.com/mongodb-shell/), [Download](https://www.mongodb.com/try/download/shell), [GitHub](https://github.com/mongodb-js/mongosh), [Introduction](https://www.mongodb.com/blog/post/introducing-the-new-shell)

```bash
mongosh <connection_string>
```

### Sample data

#### Zip code

* Download the zip file export from [docs.mongodb.com/manual/tutorial/aggregation-zip-code-data-set](https://docs.mongodb.com/manual/tutorial/aggregation-zip-code-data-set/).

* Import the data into your MongoDB server

  ```bash
  # to be run in the folder containing the json file
  mongoimport --db demoZip --collection zips --file zips.json
  # it should generate the following output
  # 2018-11-19T14:48:53.296+0100    connected to: localhost
  # 2018-11-19T14:48:53.705+0100    imported 29353 documents
  ```

* You can also import the data to your Atlas cluster

  ```bash
  mongoimport --uri "mongodb+srv://user:password@mycluster.mongodb.net/demoZip" --collection zips --file zips.json
  ```

#### dbKoda samples

* dbKoda holds a collection of sample data: [github.com/SouthbankSoftware/dbkoda-data](https://github.com/SouthbankSoftware/dbkoda-data).

### Open source tools

#### mtools

> mtools is a collection of helper scripts to parse, filter, and visualize MongoDB log files (mongod, mongos). mtools also includes mlaunch, a utility to quickly set up complex MongoDB test environments on a local machine.

More information on [github.com/rueckstiess/mtools](https://github.com/rueckstiess/mtools), [mongodb.com/blog/post/introducing-mtools](https://www.mongodb.com/blog/post/introducing-mtools).

You'll need Python (2 or 3) to install and use it.

```bash
# install with pip (Python)
pip install mtools
```

#### dbKoda

Graphical client for MongoDB databases: [dbkoda.com](https://www.dbkoda.com/) and [github.com/SouthbankSoftware/dbkoda](https://github.com/SouthbankSoftware/dbkoda).

## Deployment typologies

### MongoDB & OVH

- [FR - OVHcloud et MongoDB s’allient pour proposer une solution facilitant l’innovation des données dans le cloud](https://www.developpez.net/forums/d2109067/logiciels/solutions-d-entreprise/cloud-computing/ovhcloud-mongodb-s-allient-proposer-solution-facilitant-l-innovation-donnees-cloud/) - May 28, 2021
