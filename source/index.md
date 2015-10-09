---
title: API Reference

language_tabs:
  - javascript
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Shakespeare-In-Motion Rest API! You can use our API to access Shakespeare-In-Motion Rest API endpoints, which can get information about weekly summaries about finance, market, commodities index analysis in our database.

Rest API is cross platform, which you can use it as long as being able to send Rest request call to our server.  Most return data will be returned as JSON data format from server.  The code examples will show in JavaScript and Python. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# News Articles

## Get All news articles

```javascript
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "55ff65f3e57ca43d87d69255",
    "title": "Sample title 1",
    "content": "This is sample content 1",
    "__v": 0,
    "words_capture": ["sample","content"],
    "newsDate": "2015-09-21T02:05:39.253Z"
  },
  {
    "_id": "55ff963e1e03272096adaa42",
    "title": "Sample title 2",
    "content": "Sample content 2",
    "words_capture": ["Sample","content","2"],
    "__v": 0,
    "newsDate": "2015-09-23T05:31:42.546Z"
  }
]
```

This endpoint retrieves all news article.

### HTTP Request

`GET http://localhost:3000/api/demo/newsarticles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Create and store News Article

```javascript
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

> The above command requires to attach JSON structured in the request body:

```json
{
  "title": "Sample title 1",
  "content": "This is sample content 1",
  "words_capture": ["sample","content"],
  "newsDate": "2015-09-21T02:05:39.253Z"
}
```

This endpoint will create and store news article record to server's database.

### HTTP Request

`POST http://api/demo/newsarticles/`

### JSON data format

\* - required field

Field | Description
--------- | -----------
newsDate | The date of the news article (default is the date when the news is inserted in to the database)
*title | The title of the news article
*content | The body content of the article
url | The url of the news article
words_capture | The key words that was capture for this article

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Get a Specific News Article

```javascript
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

> The above command returns JSON structured like this:

```json
{
  "_id": "55ff65f3e57ca43d87d69255",
  "title": "Sample title 1",
  "content": "This is sample content 1",
  "__v": 0,
  "words_capture": ["sample","content"],
  "newsDate": "2015-09-21T02:05:39.253Z"
}
```

This endpoint retrieves a specific news article record.

### HTTP Request

`GET http://api/demo/newsarticles/:newsarticleId`

### URL Parameters

Parameter | Description
--------- | -----------
newsarticleId | The ID of the news article to retrieve

<aside class="notice">The newsarticleId of the news article is the primary key that the record is stored in the databse.</aside>

## Update a Specific News Article

```javascript
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

> The above command requires to attach JSON structured in the request body:

```json
{
  "title": "Sample title 1",
  "content": "This is sample content 1",
  "words_capture": ["sample","content"],
  "newsDate": "2015-09-21T02:05:39.253Z"
}
```

This endpoint update a specific news article record.

### HTTP Request

`PUT http://api/demo/newsarticles/:newsarticleId`

### URL Parameters

Parameter | Description
--------- | -----------
newsarticleId | The ID of the news article to retrieve

### JSON data format

\* - required field

Field | Description
--------- | -----------
newsDate | The date of the news article (default is the date when the news is inserted in to the database)
*title | The title of the news article
*content | The body content of the article
url | The url of the news article
words_capture | The key words that was capture for this article

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Delete a News Article

```javascript
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint delete a specific news article record.

### HTTP Request

`DELETE http://api/demo/newsarticles/:newsarticleId`

### URL Parameters

Parameter | Description
--------- | -----------
newsarticleId | The ID of the news article to delete

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

