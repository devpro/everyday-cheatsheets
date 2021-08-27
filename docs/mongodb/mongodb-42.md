# MongoDB 4.2

## New features

- [Guide to What’s New](https://www.mongodb.com/collateral/mongodb-4.2-guide-to-what-is-new)
- [Performance Boosts](https://www.mongodb.com/blog/post/mongodb-42-performance-boosts)
- [Going in](https://www.mongodb.com/blog/post/going-in-mongodb-42)

### Key highlights

- **Distributed Transactions** extending MongoDB’s multi-document ACID guarantees from replica sets to sharded clusters, enabling you to serve an ever broader range of use cases.
  - [Video](https://www.youtube.com/watch?v=iuj4Hh5EQvo&list=PL4RCxklHWZ9vG8ikkcCS94nxo0Td-Mm2s&index=3&t=7s)
- **On-Demand Materialized Views** using the new $merge operator. Caching the output of a large aggregation in a collection is a common pattern, and the new $merge operator lets you update those results efficiently instead of completely recalculating them.
  - [Blog article](https://www.mongodb.com/blog/post/coming-in-mongodb-42--ondemand-materialized-views)
- **Wildcard Indexes** make it easy and natural to model highly heterogeneous collections like product catalogs, without sacrificing great index support. You simply define a filter that automatically indexes all matching fields, sub-documents, and arrays in a collection.
  - [Video](https://www.youtube.com/watch?v=mUWZPdHopYs&list=PL4RCxklHWZ9vG8ikkcCS94nxo0Td-Mm2s&index=3)
- **MongoDB Query Language enhancements** such as more expressive updates, new math operators, and expanded regex support. update and findAndModify commands can now reference existing fields, and incorporate aggregation pipelines for even more expressivity.
  - [Blog article](https://www.mongodb.com/blog/post/coming-in-mongodb-42-pipeline-powered-updates-and-more-expressive-queries)
- **Retryable Reads and Writes**, reducing the complexity of writing code that handles transient cluster failures.

## Presentations

- [What`s new in MongoDB 4.2](https://www.mongodb.com/presentations/whats-new-in-mongodb-42) ([slides](https://docs.google.com/presentation/d/1bT6Neq7Smh6687uE_Dn7OWrWaApQfB18gkmkPmFpLOg)) - August 13, 2019

## Annoucements

- [MongoDB 4.2 is now GA: Ready for your Production Apps](https://www.mongodb.com/blog/post/mongodb-42-is-now-ga-ready-for-your-production-apps) - August 13, 2019
