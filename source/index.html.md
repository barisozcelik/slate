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

Homewhiz Cooking API Provides web-based programming interfaces that can be integrated into systems, allowing you to control and monitor users' cooking devices.

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
      "funcKey": "REMOTE_CONTROL",
      "enums": [
        "OFF",
        "ON"
      ],
      "valueType": "Boolean"
    },
    {
      "funcKey": "ATR_POWER_STATUS",
      "enums": [
        "OFF",
        "ON"
      ],
      "valueType": "OffOn"
    },
    {
      "funcKey": "STT_OPERATION_MODE",
      "enums": [
        "IDLE",
        "COOKING"
      ],
      "valueType": "Enum"
    },
    {
      "funcKey": "STT_COOKING_PHASE",
      "enums": [
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
      "valueType": "Enum_NoneVals"
    },
    {
      "funcKey": "OPT_FAN_LEVEL",
      "enums": [
        "LOW",
        "MEDIUM",
        "HIGH"
      ],
      "valueType": "Enum_OffVals"
    },
    {
      "funcKey": "STT_ELAPSE_DURATION",
      "valueType": "HoursMinutes"
    },
    {
      "funcKey": "OPT_REQUESTED_DURATION",
      "valueType": "HoursMinutes"
    }
  ]
}
```

Returns appliance function and function's options list.

### HTTP Request

`GET https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions`

<aside class="success">
Remember — You should be authenticated first!
</aside>

## Get State Of All Functions' Current Values

> returns JSON structured like this:

```json
{
  "functions": [
    {
      "funcKey": "REMOTE_CONTROL",
      "activeEnum": "ON"
    },
    {
      "funcKey": "ATR_POWER_STATUS",
      "activeEnum": "ON"
    },
    {
      "funcKey": "STT_OPERATION_MODE",
      "activeEnum": "COOKING"
    },
    {
      "funcKey": "STT_COOKING_PHASE",
      "activeEnum": "PREHEATING_PRECOOLING"
    },
    {
      "funcKey": "OPT_TEMPERATURE",
      "activeEnum": "60"
    },
    {
      "funcKey": "OPT_FAN_LEVEL",
      "activeEnum": "MEDIUM"
    },
    {
      "funcKey": "STT_ELAPSE_DURATION",
      "activeEnums": ["0","40"]
    },
    {
      "funcKey": "OPT_REQUESTED_DURATION",
      "activeEnum": ["1","20"]
    }
    
  ]
}
```

Returns function values which is currently executed.

### HTTP Request

`GET https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions/active`

<aside class="success">
Remember — You should be authenticated first!
</aside>

## Get State Of A Specific Functions

> returns JSON structured like this:

```json
{
  "funcKey": "OPT_TEMPERATURE",
  "activeEnum": "60"
}
```

Returns specific function value which is currently executed.

### HTTP Request

`GET https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions/active/{funcKey}`

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
      "funcKey": "OPT_TEMPERATURE",
      "activeEnum": "40"
    },
    {
      "funcKey": "OPT_FAN_LEVEL",
      "activeEnum": "LOW"
    },
    {
      "funcKey": "OPT_REQUESTED_DURATION",
      "activeEnums": ["2","10"]
    },
    {
      "funcKey": "CMD_CHANGE_OPERATIONAL_STATUS",
      "activeEnum": "COOK"
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

`POST https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions/active`

## Set Specific Appliance Function

> The example body JSON structured like this:

```json
{
  "funcKey": "OPT_TEMPERATURE",
  "activeEnum": "50"
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

`POST https://cooking.homewhiz.com/api/homewhizappliances/{hwid}/functions/active/{funcKey}`

