
# NodePop

## DevOps practice

[Exercise 1](http://www.onedei.com/)

[Exercise 2](http://54.175.169.80)

[Demo](http://www.onedei.com) of the methods (this link works only if you run the project)

Api for the iOS/Android apps.

## Deploy

### Install dependencies  
    
    npm install

### Configure  

Review models/db.js to set database configuration

### Init database

    npm run installDB

## Start

To start a single instance:
    
    npm start

To start in development mode:

    npm run dev (including nodemon & debug log)

## Test

    npm test (pending to create, the client specified not to do now)

## JSHint & JSCS

    npm run hints

## API v1 info


### Base Path

The API can be used with the path: 
[API V1](http://www.api.onedei.com)

### Language

All requests that return error messages are localized to english, if you want to 
change language make the request with the header accept-language set to other language, 
i.e. Accept-Language: es 

### Error example

    {
      "ok": false,
      "error": {
        "code": 401,
        "message": "Authentication failed. Wrong password."
      }
    }

### GET /anuncios

**Input Query**: 

start: {int} skip records  
limit: {int} limit to records  
sort: {string} field name to sort by  
includeTotal: {bool} whether to include the count of total records without filters  
tag: {string} tag name to filter  
venta: {bool} filter by venta or not  
precio: {range} filter by price range, examples 10-90, -90, 10-   
nombre: {string} filter names beginning with the string  

Input query example: ?start=0&limit=2&sort=precio&includeTotal=true&tag=mobile&venta=true&precio=-90&nombre=bi

**Result:** 

    {
      "ok": true,
      "result": {
        "rows": [
          {
            "_id": "55fd9abda8cd1d9a240c8230",
            "nombre": "iPhone 3GS",
            "venta": false,
            "precio": 50,
            "foto": "/images/anuncios/iphone.png",
            "__v": 0,
            "tags": [
              "lifestyle",
              "mobile"
            ]
          }
        ],
        "total": 1
      }
    }


### GET /anuncios/tags

Return the list of available tags for the resource anuncios.

**Result:** 

    {
      "ok": true,
      "allowed_tags": [
        "work",
        "lifestyle",
        "motor",
        "mobile"
      ]
    }
