# MongoDB Stitch (Legacy)

→ [docs](https://www.mongodb.com/docs/realm/stitch/index/)

## Key features

- Stitch QueryAnywhere
- Stitch Functions
- Stitch Triggers
- Stitch Mobile Sync

## SDK

- [mongodb/stitch-js-sdk](https://github.com/mongodb/stitch-js-sdk)

## Deployment

You can use GitHub Actions to setup a continuous deployment, watch this video from [Lauren Schaefer](https://www.mongodb.com/blog/post/configuring-stitch-automated-deployments-with-github).

## Getting started

You can start by this [serie of videos](https://www.mongodb.com/blog/post/start-here-a-video-introduction-to-mongodb-stitch).

### MongoDB Building a Web-based To-Do App

- Make sure [stitch-cli](https://docs.mongodb.com/stitch/import-export/stitch-cli-reference/#stitch-cli) is available:

```bash
npm install -g mongodb-stitch-cli
```

- Steps described in [docs.mongodb.com](https://docs.mongodb.com/stitch/tutorials/todo-web/):

```bash
git clone git@github.com:mongodb/stitch-examples.git
cd stitch-examples
cd todo/import/Todo_Web_App_With_Twilio
stitch-cli login --username=cloud.username@email.com --api-key=my-api-key
```

### Examples

- [mongodb/stitch-examples](https://github.com/mongodb/stitch-examples)
- [mongodb/stitch-tutorials](https://github.com/mongodb/stitch-tutorials) [mongodb/stitch-examples](https://github.com/mongodb/stitch-examples)
- [aydrian/stitchcraft-picstream](https://github.com/aydrian/stitchcraft-picstream) [MaBeuLux88/mongodb-stitch-examples](https://github.com/MaBeuLux88/mongodb-stitch-examples)
- [How I Used MongoDB Stitch to Build a Website with my Grandma’s Recipes](https://www.mongodb.com/blog/post/how-i-used-mongodb-stitch-to-build-a-website-with-my-grandmas-recipes) [GitHub](https://github.com/grammas/kitchen)

## Recipes

- [Handling Files using MongoDB Stitch and AWS S3](https://www.mongodb.com/blog/post/handling-files-using-mongodb-stitch-and-aws-s3)
- [Using AWS Rekognition to Analyse and Tag Uploaded Images Using Stitch](https://www.mongodb.com/blog/post/using-aws-rekognition-to-analyse-and-tag-uploaded-images-using-stitch)
