---
layout: post
title: Generate REST CRUD endpoints based on your ORM model.
date: 2018-01-07 00:01 +0100
categories: project
---
This is my first npm package.

- [npmjs.com/package/rest-endpoint](https://www.npmjs.com/package/rest-endpoint)
- [github.com/lucasscariot/rest-endpoint](https://github.com/lucasscariot/rest-endpoint)


## Installation
`npm install rest-endpoint --save`

`yarn add rest-endpoint --save`

## Configuration
```
const express = require('express')
const RestEndpoint = require('rest-endpoint')
const app = express()
const models = require('./models')


// Sequelize
const api = new RestEndpoint({
  app,
  sequelize: true,
  namespace: 'api',
})


// Mongoose
const api = new RestEndpoint({
  app,
  mongoose: true,
  namespace: 'api',
})

api.crud(models.channels)
api.crud(models.users)
api.crud(models.conversations)
api.crud(models.messages)
```

## Endpoints

Action  &nbsp;&nbsp;&nbsp;   | Http Method &nbsp;&nbsp;&nbsp;  | Endpoint  &nbsp;&nbsp;&nbsp; | Description &nbsp;&nbsp;&nbsp;
-----------|--------------|-------------------|------------
List       | GET          | /model            | Get a listing of records
Read       | GET          | /model/:id        | Get details about a record
Create     | POST         | /model            | Create a record
Update     | PUT          | /model/:id        | Update a record
Delete     | DELETE       | /model/:id        | Delete a record
