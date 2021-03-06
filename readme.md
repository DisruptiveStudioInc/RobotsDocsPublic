<div align="center" id="top"> 
  <img src="./.github/app.gif" alt="Apibotsv4" />

  &#xa0;

  <!-- <a href="https://apibotsv4.netlify.app">Demo</a> -->
</div>

<h1 align="center">Apibotsv4</h1>

<p align="center">
  <img alt="Github top language" src="https://img.shields.io/github/languages/top/{{YOUR_GITHUB_USERNAME}}/apibotsv4?color=56BEB8">

  <img alt="Github language count" src="https://img.shields.io/github/languages/count/{{YOUR_GITHUB_USERNAME}}/apibotsv4?color=56BEB8">

  <img alt="Repository size" src="https://img.shields.io/github/repo-size/{{YOUR_GITHUB_USERNAME}}/apibotsv4?color=56BEB8">

  <img alt="License" src="https://img.shields.io/github/license/{{YOUR_GITHUB_USERNAME}}/apibotsv4?color=56BEB8">

  <!-- <img alt="Github issues" src="https://img.shields.io/github/issues/{{YOUR_GITHUB_USERNAME}}/apibotsv4?color=56BEB8" /> -->

  <!-- <img alt="Github forks" src="https://img.shields.io/github/forks/{{YOUR_GITHUB_USERNAME}}/apibotsv4?color=56BEB8" /> -->

  <!-- <img alt="Github stars" src="https://img.shields.io/github/stars/{{YOUR_GITHUB_USERNAME}}/apibotsv4?color=56BEB8" /> -->
</p>

<!-- Status -->

<!-- <h4 align="center"> 
	🚧  Apibotsv4 🚀 Under construction...  🚧
</h4> 

<hr> -->

<p align="center">
  <a href="#dart-about">About</a> &#xa0; | &#xa0; 
  <a href="#sparkles-features">Features</a> &#xa0; | &#xa0;
  <a href="#checkered_flag-starting">Starting</a> &#xa0; | &#xa0;
</p>

<br>

## :dart: About ##

API for automated robot control and integration with external and internal backoffices

## :sparkles: Features ##

:heavy_check_mark: Manage Bussiness;\
:heavy_check_mark: Manage End Users;\
:heavy_check_mark: Manage Bots;


# Routes ##
## Register Bussiness

POST /Bussiness/Register

Body:
```json
{
  "Code": "xxx", // This code is provided by a system Admin
  "Name": "name of bussiness",
  "Home" "https://github.com/DisruptiveStudioInc", //This field is only required for disruptive dependent companies.
  "Assets": "ibot-v2", // This field is only required for disruptive dependent companies.
  "Type": 1 OR 0 // 0 = External - 1 = Internal
}
```

Successful response: 
```json
{
  "isError": false,
  "Code": "xxx"
}
```

Response Error: 
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## End User Registration
POST /Users/Register

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx"
}
```
Body:
```json
{
  "Email": "joe@example.com", // User Email
  "id": 1, // External system unique identifier
}
```
Successful response:
```json
{
  "isError": false,
  "Code": "xxx", // User Unique Identification Code
  "id": 1 // User Internal Unique Identification id
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Register Bot
POST /Bots/Register

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```
Body:
```json
{
  "Type": 1,
  "Budget": 15,
  "TransLimit": 100
}
```
Successful response:
```json
{
  "isError": false,
  "Code": "xxx", // Bot Unique Identification Code
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Update Bot Config
POST /Bots/Update

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```
Body:
```json
{
  "Budget": 15,
  "TransLimit": 100,
  "Stop": 15,
  "BotId": "sdsdsd"
}
```
Successful response:
```json
{
  "isError": false,
  "data": "Se ha actualizado correctamente el bot"
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Suspend Bot
POST /Bots/Suspend

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```
Body:
```json
{
  "Bot": "xx" // Bot unique Code
}
```
Successful response:
```json
{
  "isError": false,
  "Status": "Inactive OR Active", // Bot Unique Identification Code
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Delete Bot
**Important**: When deleting the user it is necessary to contact support because if the user has already paid for the license, he/she will lose it.

DELETE /Bots/Delete

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```
Successful response:
```json
{
  "isError": false,
  "data": "User xx has been deleted"
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```


## Change Bot Status 

POST /Bots/ChangeStatus

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```

Body:
```json
{
  "Bot": "xx" // Bot unique Code
}
```

Successful response:
```json
{
  "isError": false,
  "data": "Bot status changed"
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Get Bot Status 

POST /Bots/Status

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```

Body:
```json
{
  "Bot": "xx" // Bot unique Code
}
```

Successful response:
```json
{
  "isError": false,
  "Status": 1 // 1 = Active , 0 = Inactive
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Save or change Api Keys 

POST /Exchanges/Save

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```

Body:
```json
{
  "Bot": "xx", // Bot unique Code,
  "Exchange": 1, //1 = Binance , 2 = Binance US
  "ApiKey": "xxx",
  "ApiSecret": "xxxx"
}
```

Successful response:
```json
{
  "isError": false
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Get user ops

GET /Ops/All

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```

Successful response:
```json
{
  "isError": false,
  "data": [
    {".."},
    {".."},
    {".."},
    ...
  ]
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Get Op Fechas

POST /Ops/Fechas

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```

Body:
```json
{
  "OpId": 1,
}

```

Successful response:
```json
{
  "isError": false,
  "data": {
    Entrada: 1223344567890,
    Salida: 1234567890,
    Cancelada: 1234567890,
    Ultima: 12334567890
  } 
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Get Op Exchange

POST /Ops/Exchange

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```

Body:
```json
{
  "OpId": 1,
}

```

Successful response:
```json
{
  "isError": false,
  "data": 1 // 1 = Binance; 2 = Binance US
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## Get Op Precios

POST /Ops/Precios

Headers:
```json
{
  "Content-Type": "application/json",
  "BussinessCode": "xxx",
  "UserCode": "xxx",
  "UserId": 11111
}
```

Body:
```json
{
  "OpId": 1,
}

```

Successful response:
```json
{
  "isError": false,
  "data": {
    Entrada: 0.11,
    Salida: 0.212,
    Stop: 0.09
  }
}
```
Error response:
```json
{
  "isError": true,
  "Error": "An error occurred: description"
}
```

## :memo: License ##

This project is under license from MIT. For more details, see the [LICENSE](LICENSE.md) file.

&#xa0;

<a href="#top">Back to top</a>
