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

var data = {"title":"test title", "content":"test content"};
$http.post('/api/demo/newsarticles', $scope.news).success(function(response) {
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
  "words_capture": ["sample","content"],
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
words_capture | The key words that was capture for this article

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

`GET http://localhost:3000/api/demo/newsarticles/:newsarticleId`

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

`DELETE http://localhost:3000/api/demo/newsarticles/:newsarticleId`

### URL Parameters

Parameter | Description
--------- | -----------
newsarticleId | The ID of the news article to delete

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

#Commodity Quotes

## Get All quotes

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

This endpoint will create and store news article record to server's database.

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

This endpoint retrieves a specific news article record.

### HTTP Request

`GET http://localhost:3000/api/demo/quotes/:quoteId`

### URL Parameters

Parameter | Description
--------- | -----------
quoteId | The ID of the quote to retrieve

<aside class="notice">The quoteId of the quote is the primary key that the record is stored in the databse.</aside>

## Get quotes with time range

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
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint delete a specific quote.

### HTTP Request

`DELETE http://localhost:3000/api/demo/quotes/:quoteId`

### URL Parameters

Parameter | Description
--------- | -----------
quoteId | The ID of the quote to delete

<aside class="warning">This API is a private api, which server will only accept the requests from authenticated sources.</aside>

