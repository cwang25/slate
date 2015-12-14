---
title: API Reference

language_tabs:
  - javascript
  - python

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction

Welcome to the Shakespeare-In-Motion Rest API! You can use our API to access Shakespeare-In-Motion Rest API endpoints, which can get information about weekly summaries about finance, market, commodities index analysis in our database.

Rest API is cross platform, which you can use it as long as being able to send Rest request call to our server.  Most return data will be returned as JSON data format from server.  The code examples will show in JavaScript and Python. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# News Articles

News Article is the data that stores information about the news article that is crawled from the internet.

### Data attributes

Attribute | Description
--------- | -----------
newsDate | The date of the news article (default is the date when the news is inserted in to the database)
title | The title of the news article
content | The body content of the article
url | The url of the news article
sentiment | The sentiment of the news article
keywords | The list of the captured key words

## Get All news articles

```javascript

$http.get('http://localhost:3000/api/demo/newsarticles').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/newsarticles')

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

## Create and store News Article

```javascript

var data = {"title":"test title", "content":"test content"};
$http.post('/api/demo/newsarticles', data).success(function(response) {
    console.log(response);
});

```

```python

import requests

data = {"title":"test title", "content":"test content"}
r = requests.post('http://localhost:3000/api/demo/newsarticles', data)

```

> The above command requires to attach JSON structured in the request body:

```json
{
  "title": "Sample title 1",
  "content": "This is sample content 1",
  "keywords": ["sample","content"],
  "sentiment": "0.5",
  "newsDate": "2015-09-21T02:05:39.253Z"
}
```

This endpoint will create and store news article record to server's database.

### HTTP Request

`POST http://localhost:3000/api/demo/newsarticles/`

### JSON data format

\* - required field

Field | Description
--------- | -----------
newsDate | The date of the news article (default is the date when the news is inserted in to the database)
*title | The title of the news article
*content | The body content of the article
url | The url of the news article
sentiment | The sentiment of the news article
keywords | The list of the captured key words

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Get a News Articles with time range

```javascript

$http.get('http://localhost:3000/api/demo/newsarticles?startdate=2015-09-20&enddate=2015-09-25').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/newsarticles?startdate=2015-09-20&enddate=2015-09-25')

```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "55ff65f3e57ca43d87d69255",
    "title": "Sample title 1",
    "content": "This is sample content 1",
    "__v": 0,
    "keywords": ["sample","content"],
    "sentiment": "0.5",
    "newsDate": "2015-09-21T02:05:39.253Z"
  },
  {
    "_id": "55ff963e1e03272096adaa42",
    "title": "Sample title 2",
    "content": "Sample content 2",
    "keywords": ["Sample","content","2"],
    "sentiment": "0.5",
    "__v": 0,
    "newsDate": "2015-09-23T05:31:42.546Z"
  }
]
```

This endpoint retrieves a list of news articles that is in the given time range.

### HTTP Request

`GET http://localhost:3000/api/demo/newsbydaterange?startdate=YYYY-MM-DD&enddate=YYYY-MM-DD`

### URL Parameters

Parameter | Description
--------- | -----------
startdate | The start date of the time range
enddate | The end date of the time range

<aside class="notice">The time range of startdate and enddate will be inclusive</aside>

## Get a Specific News Article

```javascript

$http.get('http://localhost:3000/api/demo/newsarticles/55ff65f3e57ca43d87d69255').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/newsarticles/55ff65f3e57ca43d87d69255')

```

> The above command returns JSON structured like this:

```json
{
  "_id": "55ff65f3e57ca43d87d69255",
  "title": "Sample title 1",
  "content": "This is sample content 1",
  "__v": 0,
  "keywords": ["sample","content"],
  "sentiment" : "0.5",
  "newsDate": "2015-09-21T02:05:39.253Z"
}
```

This endpoint retrieves a specific news article record.

### HTTP Request

`GET http://localhost:3000/api/demo/newsarticles/:newsarticleId`

### URL Parameters

Parameter | Description
--------- | -----------
newsarticleId | The ID of the news article to retrieve

<aside class="notice">The newsarticleId of the news article is the primary key that the record is stored in the databse.</aside>

## Update a Specific News Article

```javascript

var data = {"title":"test title", "content":"test content"};
$http.put('/api/demo/newsarticles/55ff65f3e57ca43d87d69255', data).success(function(response) {
    console.log(response);
});

```

```python

import requests

data = {"title":"test title", "content":"test content"}
r = requests.put('http://localhost:3000/api/demo/newsarticles/55ff65f3e57ca43d87d69255', data)

```

> The above command requires to attach JSON structured in the request body:

```json
{
  "title": "Sample title 1",
  "content": "This is sample content 1",
  "keywords": ["sample","content"],
  "sentiment": "0.5",
  "newsDate": "2015-09-21T02:05:39.253Z"
}
```

This endpoint update a specific news article record.

### HTTP Request

`PUT http://localhost:3000/api/demo/newsarticles/:newsarticleId`

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
keywords | The key words that was capture for this article
sentiment | The sentiment of the news article

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Delete a News Article

```javascript

$http.delete('http://localhost:3000/api/demo/newsarticles/55ff65f3e57ca43d87d69255').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.delete('http://localhost:3000/api/demo/newsarticles/55ff65f3e57ca43d87d69255')

```

This endpoint delete a specific news article record.

### HTTP Request

`DELETE http://localhost:3000/api/demo/newsarticles/:newsarticleId`

### URL Parameters

Parameter | Description
--------- | -----------
newsarticleId | The ID of the news article to delete

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

#Commodity Quotes

Commodity Quotes is the data that stores the information about commodity index quote data for each day.

### Data attributes

Attribute | Description
--------- | -----------
high | The high index recorded for that quote on that date
low | The low index recorded for the quote on that date
close | The index of the quote when it is closed for the day
adj_close | The adjusted close index of the quote for the day
open | The index of the quote when it is opened for the day
symbol | The symbol/abbreviation of the quote's name on Yahoo! Finance Server
qdate | The date of the quote

## Get All quotes

```javascript

$http.get('http://localhost:3000/api/demo/quotes').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/quotes')

```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "561596c64b91f43f49260ba7",
    "high": 16865.089844,
    "volume": 120010000,
    "low": 16746.029297,
    "qdate": "2015-10-06T00:00:00.000Z",
    "close": 16790.189453,
    "symbol": "^DJI",
    "open": 16774.019531,
    "adj_close": 16790.189453,
    "__v": 0
  },
  {
    "_id": "561596c64b91f43f49260bac",
    "high": 90.389999,
    "volume": 0,
    "low": 88.43,
    "qdate": "2015-10-06T00:00:00.000Z",
    "close": 90.269997,
    "symbol": "^DJC",
    "open": 88.75,
    "adj_close": 90.269997,
    "__v": 0
  }
]
```

This endpoint retrieves all recorded quotes data.

### HTTP Request

`GET http://localhost:3000/api/demo/quotes`

## Create and store Quote

```javascript

var data = {
             "high": 90.389999,
             "volume": 0,
             "low": 88.43,
             "qdate": "2015-10-06T00:00:00.000Z",
             "close": 90.269997,
             "symbol": "^DJC",
             "open": 88.75,
             "adj_close": 90.269997
           };
$http.post('/api/demo/quotes', data).success(function(response) {
    console.log(response);
});

```

```python

import requests

data = {
         "high": 90.389999,
         "volume": 0,
         "low": 88.43,
         "qdate": "2015-10-06T00:00:00.000Z",
         "close": 90.269997,
         "symbol": "^DJC",
         "open": 88.75,
         "adj_close": 90.269997
       }
r = requests.post('http://localhost:3000/api/demo/quotes', data)

```

> The above command requires to attach JSON structured in the request body:

```json
{
  "high": 90.389999,
  "volume": 0,
  "low": 88.43,
  "qdate": "2015-10-06T00:00:00.000Z",
  "close": 90.269997,
  "symbol": "^DJC",
  "open": 88.75,
  "adj_close": 90.269997
}
```

This endpoint will create and store quote record to server's database.

### HTTP Request

`POST http://localhost:3000/api/demo/quotes/`

### JSON data format

all fields are required

Field | Description
--------- | -----------
high | The high index recorded for that quote on that date
low | The low index recorded for the quote on that date
close | The index of the quote when it is closed for the day
adj_close | The adjusted close index of the quote for the day
open | The index of the quote when it is opened for the day
symbol | The symbol/abbreviation of the quote's name on Yahoo! Finance Server
qdate | The date of the quote


<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Get a Specific Quote

```javascript

$http.get('http://localhost:3000/api/demo/quotes/561596c64b91f43f49260bac').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/quotes/561596c64b91f43f49260bac')

```

> The above command returns JSON structured like this:

```json
{
  "_id": "561596c64b91f43f49260bac",
  "high": 90.389999,
  "volume": 0,
  "low": 88.43,
  "qdate": "2015-10-06T00:00:00.000Z",
  "close": 90.269997,
  "symbol": "^DJC",
  "open": 88.75,
  "adj_close": 90.269997,
  "__v": 0
}
```

This endpoint retrieves a specific quote record.

### HTTP Request

`GET http://localhost:3000/api/demo/quotes/:quoteId`

### URL Parameters

Parameter | Description
--------- | -----------
quoteId | The ID of the quote to retrieve

<aside class="notice">The quoteId of the quote is the primary key that the record is stored in the database.</aside>

## Get quotes with time range

```javascript

$http.get('http://localhost:3000/api/demo/quotes_by_date_range?startdate=2015-09-10&enddate=2015-09-15&indexsymbol=^DJC').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/quotes_by_date_range?startdate=2015-09-10&enddate=2015-09-15&indexsymbol=^DJC')

```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "56140b96704afaca3a822c88",
    "high": 88.889999,
    "volume": 0,
    "low": 88.400002,
    "qdate": "2015-09-15T00:00:00.000Z",
    "close": 88.57,
    "symbol": "^DJC",
    "open": 88.839996,
    "adj_close": 88.57,
    "__v": 0
  },
  {
    "_id": "56140b96704afaca3a822c89",
    "high": 89.32,
    "volume": 0,
    "low": 88.349998,
    "qdate": "2015-09-14T00:00:00.000Z",
    "close": 88.57,
    "symbol": "^DJC",
    "open": 89.309998,
    "adj_close": 88.57,
    "__v": 0
  },
  {
    "_id": "56140b96704afaca3a822c8a",
    "high": 89.199997,
    "volume": 0,
    "low": 87.879997,
    "qdate": "2015-09-11T00:00:00.000Z",
    "close": 88.93,
    "symbol": "^DJC",
    "open": 89.120003,
    "adj_close": 88.93,
    "__v": 0
  },
  {
    "_id": "56140b96704afaca3a822c8b",
    "high": 89.269997,
    "volume": 0,
    "low": 87.949997,
    "qdate": "2015-09-10T00:00:00.000Z",
    "close": 89.150002,
    "symbol": "^DJC",
    "open": 88.279999,
    "adj_close": 89.150002,
    "__v": 0
  }
]
```

This endpoint retrieves a list of quotes that is in the given time range.

### HTTP Request

`GET http://localhost:3000/api/demo/quotes_by_date_range?startdate=YYYY-MM-DD&enddate=YYYY-MM-DD&indexsymbol=XX`

### URL Parameters

\* - required parameter

Parameter | Description
--------- | -----------
startdate* | The start date of the time range
enddate* | The end date of the time range
indexsymbol | Optional parameter which allows returned data to be filtered with desired symbol such as only retrieving quotes of Bloomberg Commodity Index (^DJC).

<aside class="notice">The time range of startdate and enddate will be inclusive</aside>

## Update a Specific Quote

```javascript

var data = {
             "high": 90.389999,
             "volume": 0,
             "low": 88.43,
             "qdate": "2015-10-06T00:00:00.000Z",
             "close": 90.269997,
             "symbol": "^DJC",
             "open": 88.75,
             "adj_close": 90.269997
           };
$http.put('/api/demo/quotes/56140b96704afaca3a822c8b', data).success(function(response) {
    console.log(response);
});

```

```python

import requests

data = {
         "high": 90.389999,
         "volume": 0,
         "low": 88.43,
         "qdate": "2015-10-06T00:00:00.000Z",
         "close": 90.269997,
         "symbol": "^DJC",
         "open": 88.75,
         "adj_close": 90.269997
       }
r = requests.put('http://localhost:3000/api/demo/quotes/56140b96704afaca3a822c8b', data)

```

> The above command requires to attach JSON structured in the request body:

```json
{
  "high": 90.389999,
  "volume": 0,
  "low": 88.43,
  "qdate": "2015-10-06T00:00:00.000Z",
  "close": 90.269997,
  "symbol": "^DJC",
  "open": 88.75,
  "adj_close": 90.269997
}
```

This endpoint update a specific quote record.

### HTTP Request

`PUT http://localhost:3000/api/demo/quotes/:quoteId`

### URL Parameters

Parameter | Description
--------- | -----------
newsarticleId | The ID of the news article to update

### JSON data format

all fields are required

Field | Description
--------- | -----------
high | The high index recorded for that quote on that date
low | The low index recorded for the quote on that date
close | The index of the quote when it is closed for the day
adj_close | The adjusted close index of the quote for the day
open | The index of the quote when it is opened for the day
symbol | The symbol/abbreviation of the quote's name on Yahoo! Finance Server
qdate | The date of the quote

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Delete a Quote

```javascript

$http.delete('http://localhost:3000/api/demo/quotes/56140b96704afaca3a822c8b').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.delete('http://localhost:3000/api/demo/quotes/56140b96704afaca3a822c8b')

```

This endpoint deletes a specific quote.

### HTTP Request

`DELETE http://localhost:3000/api/demo/quotes/:quoteId`

### URL Parameters

Parameter | Description
--------- | -----------
quoteId | The ID of the quote to delete

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>



## Get Quotes with Symbol

```javascript

$http.get('http://localhost:3000/api/demo/quotes_by_symbol?indexsymbol=^DJC').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/quotes_by_symbol?indexsymbol=^DJC')

```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "56140b96704afaca3a822c88",
    "high": 88.889999,
    "volume": 0,
    "low": 88.400002,
    "qdate": "2015-09-15T00:00:00.000Z",
    "close": 88.57,
    "symbol": "^DJC",
    "open": 88.839996,
    "adj_close": 88.57,
    "__v": 0
  },
  {
    "_id": "56140b96704afaca3a822c89",
    "high": 89.32,
    "volume": 0,
    "low": 88.349998,
    "qdate": "2015-09-14T00:00:00.000Z",
    "close": 88.57,
    "symbol": "^DJC",
    "open": 89.309998,
    "adj_close": 88.57,
    "__v": 0
  },
  {
    "_id": "56140b96704afaca3a822c8a",
    "high": 89.199997,
    "volume": 0,
    "low": 87.879997,
    "qdate": "2015-09-11T00:00:00.000Z",
    "close": 88.93,
    "symbol": "^DJC",
    "open": 89.120003,
    "adj_close": 88.93,
    "__v": 0
  },
  {
    "_id": "56140b96704afaca3a822c8b",
    "high": 89.269997,
    "volume": 0,
    "low": 87.949997,
    "qdate": "2015-09-10T00:00:00.000Z",
    "close": 89.150002,
    "symbol": "^DJC",
    "open": 88.279999,
    "adj_close": 89.150002,
    "__v": 0
  }
]
```

This endpoint retrieves a list of quotes that have a given market ticker symbol (ex. ^DJC).

### HTTP Request

`GET http://localhost:3000/api/demo/quotes_by_symbol?indexsymbol=XX`

### URL Parameters



Parameter | Description
--------- | -----------
indexsymbol | A market ticker symbol





# Entities

Entities is the data that stores the information about captured entities for each day.

### Data attributes

Attribute | Description
--------- | -----------
entityDate | The date of the entity (default is the date when the entity is inserted in to the database)
text | The entity's name
count | The number of times the entity appears in a week's news
sentiment | A value which indicates to what extent an entity was mentioned in a positive or negative tone in the news. Values range from -1 (very negative) to +1 (very positive)


## Get All Entities

```javascript

$http.get('http://localhost:3000/api/demo/entity').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/entity')

```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "55ff65f3e57ca43d87d69255",
    "entityDate": "2015-12-12T00:00:00.000Z",
    "text": "Federal Reserve",
    "count": 10,
    "sentiment": 0.5

  },
  {
    "_id": "55ff65f3e57ca43d87d69259",
    "entityDate": "2015-12-12T00:00:00.000Z",
    "text": "Inflation",
    "count": 7,
    "sentiment": -0.25
  }
]
```

This endpoint retrieves all entities.

### HTTP Request

`GET http://localhost:3000/api/demo/entity`

## Create and Store Entities

```javascript

var data = {"entityDate":"2015-12-12", "text":"Federal Reserve", "count":10, "sentiment":0.5};
$http.post('/api/demo/entity', data).success(function(response) {
    console.log(response);
});

```

```python

import requests

data = {"entityDate":"2015-12-12T00:00:00.000Z", "text":"Federal Reserve", "count":10, "sentiment":0.5}
r = requests.post('http://localhost:3000/api/demo/entity', data)

```

> The above command requires to attach JSON structured in the request body:

```json
{
  "_id": "55ff65f3e57ca43d87d69255",
  "entityDate": "2015-12-12T00:00:00.000Z",
  "text": "Federal Reserve",
  "count": 10,
  "sentiment": 0.5
}
```

This endpoint will create and store entity records to the server's database.

### HTTP Request

`POST http://localhost:3000/api/demo/entity/`

### JSON data format

\* - required field

Field | Description
--------- | -----------
entityDate | The date of the entity (default is the date when the entity is inserted in to the database)
*text | The entity's name
*count | The number of times the entity appears in a week's news
sentiment | A value which indicates to what extent an entity was mentioned in a positive or negative tone in the news. Values range from -1 (very negative) to +1 (very positive)


<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Get an Entity within Time Range

```javascript

$http.get('http://localhost:3000/api/demo/entitiesbydaterange?startdate=2015-11-16&enddate=2015-11-17').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/entitiesbydaterange?startdate=2015-11-16&enddate=2015-11-17')

```

> The above command returns JSON structured like this:

```json
[
  {
      "_id": "55ff65f3e57ca43d87d69255",
      "entityDate": "2015-11-16T00:00:00.000Z",
      "text": "Federal Reserve",
      "count": 10,
      "sentiment": 0.5

    },
    {
      "_id": "55ff65f3e57ca43d87d69259",
      "entityDate": "2015-11-17T00:00:00.000Z",
      "text": "Inflation",
      "count": 7,
      "sentiment": -0.25
    }
]
```

This endpoint retrieves a list of entities that are in the given time range.

### HTTP Request

`GET http://localhost:3000/api/demo/entitiesbydaterange?startdate=YYYY-MM-DD&enddate=YYYY-MM-DD`

### URL Parameters

Parameter | Description
--------- | -----------
startdate | The start date of the time range
enddate | The end date of the time range

<aside class="notice">The time range of startdate and enddate will be inclusive</aside>

## Get a Specific Entity

```javascript

$http.get('http://localhost:3000/api/demo/entity/55ff65f3e57ca43d87d69255').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/entity/55ff65f3e57ca43d87d69255')

```

> The above command returns JSON structured like this:

```json
  {
      "_id": "55ff65f3e57ca43d87d69255",
      "entityDate": "2015-11-16T00:00:00.000Z",
      "text": "Federal Reserve",
      "count": 10,
      "sentiment": 0.5

  }
```

This endpoint retrieves a specific entity record.

### HTTP Request

`GET http://localhost:3000/api/demo/entity/:entityId`

### URL Parameters

Parameter | Description
--------- | -----------
entityId | The ID of the entity to retrieve

<aside class="notice">The entityId is the primary key of the record stored in the database.</aside>

## Update a Specific Entity

```javascript

var data = {"entityDate":"2015-12-12", "text":"Federal Reserve", "count":10, "sentiment":0.5};
$http.put('/api/demo/entity/55ff65f3e57ca43d87d69255', data).success(function(response) {
    console.log(response);
});

```

```python

import requests

data = {"entityDate":"2015-12-12", "text":"Federal Reserve", "count":10, "sentiment":0.5}
r = requests.put('http://localhost:3000/api/demo/entity/55ff65f3e57ca43d87d69255', data)

```

> The above command requires to attach JSON structured in the request body:

```json
    {
      "_id": "55ff65f3e57ca43d87d69255",
      "entityDate": "2015-11-16T00:00:00.000Z",
      "text": "Federal Reserve",
      "count": 10,
      "sentiment": 0.5

    }
```

This endpoint update a specific entity record.

### HTTP Request

`PUT http://localhost:3000/api/demo/entity/:entityId`

### URL Parameters

Parameter | Description
--------- | -----------
entityId | The ID of the entity to retrieve

### JSON data format

\* - required field

Field | Description
--------- | -----------
entityDate | The date of the entity (default is the date when the entity is inserted in to the database)
*text | The entity's name
*count | The number of times the entity appears in a week's news
sentiment | A value which indicates to what extent an entity was mentioned in a positive or negative tone in the news. Values range from -1 (very negative) to +1 (very positive)

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Delete an Entity

```javascript

$http.delete('http://localhost:3000/api/demo/entity/55ff65f3e57ca43d87d69255').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.delete('http://localhost:3000/api/demo/entity/55ff65f3e57ca43d87d69255')

```

This endpoint deletes a specific entity record.

### HTTP Request

`DELETE http://localhost:3000/api/demo/entity/:entityId`

### URL Parameters

Parameter | Description
--------- | -----------
entityId | The ID of the entity to delete

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>



# Week Summary

Week Summary is the data that stores the summarized data for each week, such as week momentum and week index quote RSI indicator.

### Data Attributes

Attribute | Description
--------- | -----------
week_start_date | The starting date of a week
week_end_date | The ending date of a week
week_index | A market ticker symbol(default is "^DJC")
bcom_indices | An array of IDs for market quote records
bcom_max | The market index's highest value within a week
bcom_min | The market index's lowest value within a week
bcom_avg_slope | The market index's slope value for the week
bcom_week_momentum | The market index's momentum indicator value for the week
bcom_rsi | The market index's Relative Strength Indicator value for the week
articles | An array of IDs for news article records
avg_article_sentiment | The average of all the sentiment field values in the array of articles

## Get All Week Summaries

```javascript

$http.get('http://localhost:3000/api/demo/weeksum').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/weeksum')

```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "55ff65f3e57ca43d87d69259",
    "week_start_date":"2015-11-16:T00:00:00.000Z",
    "week_end_date":"2015-11-20:T00:00:00.000Z",
    "week_index":"^DJC",
    "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
    "bcom_max":81.75,
    "bcom_min":80.37,
    "bcom_avg_slope":-0.15,
    "bcom_week_momentum":0.62,
    "bcom_rsi":40.8,
    "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
    "avg_article_sentiment":0.25
  },
  {
     "_id": "55ff65f3e57ca43d87d69260",
     "week_start_date":"2015-11-09:T00:00:00.000Z",
     "week_end_date":"2015-11-13:T00:00:00.000Z",
     "week_index":"^DJC",
     "bcom_indices":["55ff65f3e50","55ff65f3e51","55ff65f3e52","55ff65f3e53","55ff65f3e54"],
     "bcom_max":82.46,
     "bcom_min":81.42,
     "bcom_avg_slope":0.26,
     "bcom_week_momentum":-1.04,
     "bcom_rsi":87.68,
     "articles":["55ff65f3e40","55ff65f3e41","55ff65f3e42","55ff65f3e43","55ff65f3e44"],
     "avg_article_sentiment":0.30
  }
]
```

This endpoint retrieves all week summaries.

### HTTP Request

`GET http://localhost:3000/api/demo/weeksum`

## Create and Store Week Summaries

```javascript

var data = {"week_start_date":"2015-11-16:T00:00:00.000Z",
            "week_end_date":"2015-11-20:T00:00:00.000Z",
            "week_index":"^DJC",
            "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
            "bcom_max":81.75,
            "bcom_min":80.37,
            "bcom_avg_slope":-0.15,
            "bcom_week_momentum":0.62,
            "bcom_rsi":40.8,
            "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
            "avg_article_sentiment":0.25};
$http.post('/api/demo/weeksum', data).success(function(response) {
    console.log(response);
});

```

```python

import requests

data = {
            "week_start_date":"2015-11-16:T00:00:00.000Z",
            "week_end_date":"2015-11-20:T00:00:00.000Z",
            "week_index":"^DJC",
            "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
            "bcom_max":81.75,
            "bcom_min":80.37,
            "bcom_avg_slope":-0.15,
            "bcom_week_momentum":0.62,
            "bcom_rsi":40.8,
            "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
            "avg_article_sentiment":0.25}
r = requests.post('http://localhost:3000/api/demo/weeksum', data)

```

> The above command requires to attach JSON structured in the request body:

```json
{             "_id": "55ff65f3e58",
              "week_start_date":"2015-11-16:T00:00:00.000Z",
              "week_end_date":"2015-11-20:T00:00:00.000Z",
              "week_index":"^DJC",
              "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
              "bcom_max":81.75,
              "bcom_min":80.37,
              "bcom_avg_slope":-0.15,
              "bcom_week_momentum":0.62,
              "bcom_rsi":40.8,
              "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
              "avg_article_sentiment":0.25
}
```

This endpoint will create and store week summary records to the server's database.

### HTTP Request

`POST http://localhost:3000/api/demo/weeksum/`

### JSON data format

\* - required field

Field | Description
--------- | -----------
*week_start_date | The starting date of a week
*week_end_date | The ending date of a week
week_index | A market ticker symbol(default is "^DJC")
bcom_indices | An array of IDs for market quote records
*bcom_max | The market index's highest value within a week
*bcom_min | The market index's lowest value within a week
*bcom_avg_slope | The market index's slope value for the week
bcom_week_momentum | The market index's momentum indicator value for the week
bcom_rsi | The market index's Relative Strength Indicator value for the week
articles | An array of IDs for news article records
avg_article_sentiment | The average of all the sentiment field values in the array of articles

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>



## Get Week Summary with Date

```javascript

$http.get('http://localhost:3000/api/demo/weeksum_by_date_index?date=2015-11-16&indexsymbol=^DJC').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/weeksum_by_date_index?date=2015-11-16&indexsymbol=^DJC')

```

> The above command returns JSON structured like this:

```json
[
  {             "_id": "55ff65f3e58",
                "week_start_date":"2015-11-16:T00:00:00.000Z",
                "week_end_date":"2015-11-20:T00:00:00.000Z",
                "week_index":"^DJC",
                "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
                "bcom_max":81.75,
                "bcom_min":80.37,
                "bcom_avg_slope":-0.15,
                "bcom_week_momentum":0.62,
                "bcom_rsi":40.8,
                "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
                "avg_article_sentiment":0.25
  }
]
```

This endpoint retrieves a week summary for a week that includes the date specified by a URL parameter.

### HTTP Request

`GET http://localhost:3000/api/demo/weeksum_by_date_index?startdate=YYYY-MM-DD&enddate=YYYY-MM-DD`

### URL Parameters

Parameter | Description
--------- | -----------
*date | The date which the returned week summary should include. Entering a Saturday date will return a week summary for the preceding Monday-Friday period. Entering a Sunday date will return a week summary for the upcoming Monday-Friday period.
indexsymbol | A market ticker symbol (ex. "^DJC")


## Get a Specific Week Summary

```javascript

$http.get('http://localhost:3000/api/demo/weeksum/55ff65f3e58').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/weeksum/55ff65f3e58')

```

> The above command returns JSON structured like this:

```json
  {
    "_id": "55ff65f3e58",
    "week_start_date":"2015-11-16:T00:00:00.000Z",
    "week_end_date":"2015-11-20:T00:00:00.000Z",
    "week_index":"^DJC",
    "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
    "bcom_max":81.75,
    "bcom_min":80.37,
    "bcom_avg_slope":-0.15,
    "bcom_week_momentum":0.62,
    "bcom_rsi":40.8,
    "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
    "avg_article_sentiment":0.25

  }
```

This endpoint retrieves a specific week summary record.

### HTTP Request

`GET http://localhost:3000/api/demo/weeksum:weeksumId`

### URL Parameters

Parameter | Description
--------- | -----------
weeksumId | The ID of the week summary to retrieve

<aside class="notice">weeksumID is the primary key of the record stored in the database.</aside>

## Update a Specific Week Summary

```javascript

var data = {
            "week_start_date":"2015-11-16:T00:00:00.000Z",
            "week_end_date":"2015-11-20:T00:00:00.000Z",
            "week_index":"^DJC",
            "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
            "bcom_max":81.75,
            "bcom_min":80.37,
            "bcom_avg_slope":-0.15,
            "bcom_week_momentum":0.62,
            "bcom_rsi":40.8,
            "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
            "avg_article_sentiment":0.25};
$http.put('/api/demo/weeksum/55ff65f3e58', data).success(function(response) {
    console.log(response);
});

```

```python

import requests

data = {
        "week_start_date":"2015-11-16:T00:00:00.000Z",
        "week_end_date":"2015-11-20:T00:00:00.000Z",
        "week_index":"^DJC",
        "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
        "bcom_max":81.75,
        "bcom_min":80.37,
        "bcom_avg_slope":-0.15,
        "bcom_week_momentum":0.62,
        "bcom_rsi":40.8,
        "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
        "avg_article_sentiment":0.25}
r = requests.put('http://localhost:3000/api/demo/weeksum/55ff65f3e58', data)

```

> The above command requires to attach JSON structured in the request body:

```json
    {

              "_id": "55ff65f3e58",
              "week_start_date":"2015-11-16:T00:00:00.000Z",
              "week_end_date":"2015-11-20:T00:00:00.000Z",
              "week_index":"^DJC",
              "bcom_indices":["55ff65f3e60","55ff65f3e61","55ff65f3e62","55ff65f3e63","55ff65f3e64"],
              "bcom_max":81.75,
              "bcom_min":80.37,
              "bcom_avg_slope":-0.15,
              "bcom_week_momentum":0.62,
              "bcom_rsi":40.8,
              "articles":["55ff65f3e70","55ff65f3e71","55ff65f3e72","55ff65f3e73","55ff65f3e74"],
              "avg_article_sentiment":0.25

    }
```

This endpoint updates a specific week summary record.

### HTTP Request

`PUT http://localhost:3000/api/demo/weeksum/:weeksumId`

### URL Parameters

Parameter | Description
--------- | -----------
weeksumId | The ID of the week summary to retrieve

### JSON data format

\* - required field

Field | Description
--------- | -----------
*week_start_date | The starting date of a week
*week_end_date | The ending date of a week
week_index | A market ticker symbol(default is "^DJC")
bcom_indices | An array of IDs for market quote records
*bcom_max | The market index's highest value within a week
*bcom_min | The market index's lowest value within a week
*bcom_avg_slope | The market index's slope value for the week
bcom_week_momentum | The market index's momentum indicator value for the week
bcom_rsi | The market index's Relative Strength Indicator value for the week
articles | An array of IDs for news article records
avg_article_sentiment | The average of all the sentiment field values in the array of articles


<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

## Delete a Week Summary

```javascript

$http.delete('http://localhost:3000/api/demo/weeksum/55ff65f3e58').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.delete('http://localhost:3000/api/demo/weeksum/55ff65f3e58')

```

This endpoint deletes a specific week summary record.

### HTTP Request

`DELETE http://localhost:3000/api/demo/weeksum/:weeksumId`

### URL Parameters

Parameter | Description
--------- | -----------
weeksumId | The ID of the week summary to delete

<aside class="warning">This API is a private api, for which the server will only accept requests from authenticated sources.</aside>


# Get News from Alchemy

## Get News from Alchemy

```javascript

$http.get('http://localhost:3000/api/demo/get_news_from_alchemy?startdate=2015-11-16&enddate=2015-11-20').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/get_news_from_alchemy?startdate=2015-11-16&enddate=2015-11-20')

```


This endpoint runs the ArticleCrawler.py and ArticleDatabaseClean.py Python scripts to access the Alchemy API to obtain news.

### HTTP Request

`GET http://localhost:3000/api/demo/get_news_from_alchemy?startdate=YYYY-MM-DD&enddate=YYYY-MM-DD`




# Get Week Summary

## Crawl and Generate Week Summary

```javascript

$http.get('http://localhost:3000/api/demo/crawl_and_generate_week_summary?startdate=2015-11-16&enddate=2015-11-20').success(function (response) {
    console.log(response);
});

```

```python

import requests

r = requests.get('http://localhost:3000/api/demo/crawl_and_generate_week_summary?startdate=2015-11-16&enddate=2015-11-20')

```


This endpoint runs the IndexCrawler.py Python script to obtain market quotes from Yahoo Finance Server. After the market quotes have been retrieved, a week summary is generated and stored in the database.

### HTTP Request

`GET http://localhost:3000/api/demo/crawl_and_generate_week_summary?startdate=YYYY-MM-DD&enddate=YYYY-MM-DD`

