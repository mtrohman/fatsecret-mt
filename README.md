# Fat Secret Unofficial API

This are unofficial http interface to [Fat Secret](fatsecret.com) food databases. The API will show you information related about the food you're looking for. Remember that this are *unofficial*. Please report if something broken.

## Features

Here are some feature that this API offers you

### Multi Lang Multi Food

Some food are only available on your language, since Fat Secret had many [languages](https://www.fatsecret.co.id/Default.aspx?pa=sites) I tried to implement it as multi lang. However it still need some work. Since I only speak English and Indonesia for now it only support those two. You can make a pull request support your language!

### Search Food

To search food, you can do this:

```http
GET api/:lang/search?query=tempe&page=0

# query: name of your food
# page: go to current page
```

Example `JSON Response` :

```json
{
  "items":[
    {
      "title":"Tempe Goreng",
      "protein":2,
      "fat":2.28,
      "carbo":1.79,
      "calories":34,
      "serving":"per 1 buah",
      "detailLink":"https://fatsecret-mt.vercel.app/api/id/detail?url=%2Fkalori-gizi%2Fumum%2Ftempe-goreng"
    },
    {
      "title":"Tempe",
      "protein":18.54,
      "fat":10.8,
      "carbo":9.39,
      "calories":193,
      "serving":"per 100 gram",
      "detailLink":"https://fatsecret-mt.vercel.app/api/id/detail?url=%2Fkalori-gizi%2Fumum%2Ftempe"
    },
    {
      "title":"Tempe Orek",
      "protein":13.11,
      "fat":8.2,
      "carbo":15.6,
      "calories":175,
      "serving":"per 100 gram",
      "detailLink":"https://fatsecret-mt.vercel.app/api/id/detail?url=%2Fkalori-gizi%2Fumum%2Ftempe-orek"
    },
    {
      "title":"Tempe Rebus",
      "protein":18.19,
      "fat":11.38,
      "carbo":9.35,
      "calories":196,
      "serving":"per 100 gram",
      "detailLink":"https://fatsecret-mt.vercel.app/api/id/detail?url=%2Fkalori-gizi%2Fumum%2Ftempe-rebus"
    },
    {
      "title":"Tempe Bacem",
      "protein":3.73,
      "fat":3.1,
      "carbo":2.23,
      "calories":49,
      "serving":"per 1 potong",
      "detailLink":"https://fatsecret-mt.vercel.app/api/id/detail?url=%2Fkalori-gizi%2Fumum%2Ftempe-bacem"
    },
    {
      "title":"Tempe Mendoan",
      "protein":11.18,
      "fat":12.78,
      "carbo":12.69,
      "calories":200,
      "serving":"per 100 gram",
      "detailLink":"https://fatsecret-mt.vercel.app/api/id/detail?url=%2Fkalori-gizi%2Fumum%2Ftempe-mendoan"
    }
  ],
  "total":21,
  "prev":0,
  "next":1,
  "current":0
}
```

### Food Detail [WIP]

Print the detail of food that you're looking for

```http
GET api/:lang/detail?url=%2Fkalori-gizi%2Fumum%2Ftempe

# url: URL of detailLink acquired from search request
```

Example `JSON Response` :

```json
{
  "name":"Tempe",
  "portion":"100 gram (g)",
  "energy":{
    "val":"808",
    "unit":"kj"
  },
  "calorie":{
    "val":"193",
    "unit":"kkal"
  },
  "fat":{
    "val":"10.8",
    "unit":"g"
  },
  "saturated_fat":{
    "val":"2.22",
    "unit":"g"
  },
  "colestrol":{
    "val":"0",
    "unit":"mg"
  },
  "protein":{
    "val":"18.54",
    "unit":"g"
  },
  "carbohydrate":{
    "val":"9.39",
    "unit":"g"
  },
  "sodium":{
    "val":"9",
    "unit":"mg"
  },
  "serving_size":[
    {
      "val":"37697",
      "text":"mangkok"
    },
    {
      "val":"61054",
      "text":"gram (g)"
    }
  ],
  "debug":"https://www.fatsecret.co.id/kalori-gizi/umum/tempe"
}
```

## Contribute

### Contribute to your own language

To make your language _plugin_ you could add to the settings [here](./utils/lang) let me explain whare are those config

```js
{
  lang: 'specify your language abbreviation',
  menuUrl: 'home page menu for foods',
  searchUrl: 'search url for fat secret',
  otherSizes: 'this are text that you will find 2 lines under the food name after you search food'
}
```

## Development

```
$ npm i -g vercel
$ vercel start
```