---
title: Homewhiz Cooking API

language_tabs: # must be one of https://git.io/vQNgJ
  - json
  # - python

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  # - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Homewhiz Cooking API! 

HomeWhiz is a IoT platform for Arcelik Group's smart home technology. 

Homewhiz Cooking API provides web-based programming interfaces that can be consumed by external systems, allowing you to control and monitor users' cooking devices.

# Authentication

To use Homewhiz Cooking API, first user must be authenticated. [HomeWhiz Authentication Server](http://auth.homewhiz.com) provides JWT token if user pass the authentication process.


# Account Information

## Get My Appliances

> returns JSON structured like this:

```json
{
  "appliances": [
    {
      "name": "Oven One",
      "applianceId": "ADCD878956",
      "type": "Oven"
    },
    {
      "name": "Oven Two",
      "applianceId": "ADCD878957",
      "type": "Oven"
    }
  ]
}
```

This endpoint returns a list of all homewhiz appliances which are paired with the logged-in user account.

### HTTP Request

`GET https://cooking.homewhiz.com/api/homewhizappliances`

<aside class="success">
Remember — You should be authenticated first!
</aside>

## Get Specific Appliances

> returns JSON structured like this:

```json
{
  "name": "Oven One",
  "applianceId": "ADCD878956",
  "type": "Oven"
}
```

Returns a specific homewhiz appliance which is paired with the logged-in user account.

### HTTP Request

`GET https://cooking.homewhiz.com/api/homewhizappliances/{hwid}`

<aside class="success">
Remember — You should be authenticated first!
</aside>

# Retrieving Information
## Get All Functions

> returns JSON structured like this:

```json
{
  "functions": [
    {
      "func": "REMOTE_CONTROL",
      "enums": [
        "OFF",
        "ON"
      ],
      "valueType": "Enum"
    },
    {
      "func": "ATR_POWER_STATUS",
      "enums": [
        "OFF",
        "ON"
      ],
      "valueType": "Enum"
    },
    {
      "func": "STT_OPERATION_MODE",
      "enums": [
        "IDLE",
        "COOKING"
      ],
      "valueType": "Enum"
    },
    {
      "func": "STT_COOKING_PHASE",
      "enums": [
        "NONE",
        "PREHEATING_PRECOOLING",
        "COOKING",
        "PAUSED",
        "CANCELLING",
        "CANCELLED",
        "FINISHED",
        "COOKING_MORE",
        "PREPARING_STEAM",
        "SPRAYING_STEAM"
      ],
      "valueType": "Enum"
    },
    {
      "func": "OPT_TEMPERATURE",
      "valueType": "DegreeCelsius",
      "lowerLimit": 40,
      "upperLimit": 320,
      "step": 5
    }
    {
      "func": "OPT_FAN_LEVEL",
      "enums": [
        "OFF",
        "LOW",
        "MEDIUM",
        "HIGH"
      ],
      "valueType": "Enum"
    },
    {
      "func": "STT_ELAPSE_DURATION",
      "valueType": "HoursMinutes"
    },
    {
      "func": "OPT_REQUESTED_DURATION",
      "valueType": "HoursMinutes"
    }
  ]
}
```

Returns appliance function and function's options list.

### HTTP Request

`GET https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/meta/availablefunctions`

<aside class="success">
Remember — You should be authenticated first!
</aside>

## Get State Of All Functions' Current Values

> returns JSON structured like this:

```json
{
  "functions": [
    {
      "func": "REMOTE_CONTROL",
      "val": "ON"
    },
    {
      "func": "ATR_POWER_STATUS",
      "val": "ON"
    },
    {
      "func": "STT_OPERATION_MODE",
      "val": "COOKING"
    },
    {
      "func": "STT_COOKING_PHASE",
      "val": "PREHEATING_PRECOOLING"
    },
    {
      "func": "OPT_TEMPERATURE",
      "val": "60"
    },
    {
      "func": "OPT_FAN_LEVEL",
      "val": "MEDIUM"
    },
    {
      "func": "STT_ELAPSE_DURATION",
      "val": "00.40"
    },
    {
      "func": "OPT_REQUESTED_DURATION",
      "val": "01.20"
    }
    
  ]
}
```

Returns function values which is currently executed.

### HTTP Request

`GET https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions`

<aside class="success">
Remember — You should be authenticated first!
</aside>

## Get State Of A Specific Functions

> returns JSON structured like this:

```json
{
  "func": "OPT_TEMPERATURE",
  "val": "60"
}
```

Returns specific function value which is currently executed.

### HTTP Request

`GET https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions/{func}`

<aside class="success">
Remember — You should be authenticated first!
</aside>

# Sending Information

## Set Appliance Functions

> The example body JSON structured like this:

```json
{
  "functions": [
    ,
    {
      "func": "OPT_TEMPERATURE",
      "val": "40"
    },
    {
      "func": "OPT_FAN_LEVEL",
      "val": "LOW"
    },
    {
      "func": "OPT_REQUESTED_DURATION",
      "val": "02.10"
    },
    {
      "func": "CMD_CHANGE_OPERATIONAL_STATUS",
      "val": "COOK"
    }
  ]
}


```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully sent functions",
  "data": null
}
```

This endpoint sets multiple functions.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions`

## Set Specific Appliance Function

> The example body JSON structured like this:

```json
{
  "func": "OPT_TEMPERATURE",
  "val": "50"
}


```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully sent function",
  "data": null
}
```

This endpoint sets specific function.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions/{func}`

