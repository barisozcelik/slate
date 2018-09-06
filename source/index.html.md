---
title: ProCAM Supplier API

language_tabs: # must be one of https://git.io/vQNgJ
  - json
  # - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the ProCAM Supplier API! 

ProCAM is a cloud service that provides a variety of product description information, configurations and text / visual content for IoT devices serviced within the Arçelik IOT Platform to provide and manage client IoT devices and mobile applications

ProCAM Supplier API Provides web-based programming interfaces that can be integrated between systems, enabling the system to be included in various corporate workflows by enabling the content feeding by intra-Arçelik enterprise systems and non-Arçelik business partners' systems.

# Authentication

ProCAM Supplier API uses API keys to allow access to the API. You can register a new ProCAM Supplier API API key at our [developer portal](http://example.com/developers).

ProCAM Supplier API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Program Pool

## Get All Program keys for a specific appliance type

> returns JSON structured like this:

```json
[
  {
    "id": 1,
    "applianceType": "Washer",
    "programStrKey": "WASHER_PROGRAM_ECO_50"
  },
  {
    "id": 2,
    "applianceType": "Washer",
    "programStrKey": "WASHER_PROGRAM_WOOL"
  }
]
```

This endpoint retrieves all programs of a specific appliance type.

### HTTP Request

`GET https://procam.arcelikiot.com/api/program-pool`

### Query Parameters

Parameter | Description
--------- |  -----------
applianceType | Define a specific appliance type(Washer, Refrigerator, Dishwasher, Oven, Dryer ..)

<aside class="success">
Remember — You should be authenticated first!
</aside>

## Insert a new Program

> The example body JSON structured like this:

```json
[
  {
    "applianceType": "Washer",
    "programStrKey": "WASHER_PROGRAM_ECO_50"
  }
]

```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully inserted programs",
  "data": null
}
```

This endpoint inserts new programs.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`POST https://procam.arcelikiot.com/api/program-pool`

# SubProgram Pool

## Get All SubProgram keys for a specific appliance type

> returns JSON structured like this:

```json
[
  {
    "id": 1,
    "applianceType": "Washer",
    "subprogramStrKey": "WASHER_SPIN",
  },
  {
    "id": 2,
    "applianceType": "Washer",
    "subprogramStrKey": "WASHER_LIQUID_DETERGENT"
  }
]
```

This endpoint retrieves all subprograms of a specific appliance type.

### HTTP Request

`GET https://procam.arcelikiot.com/api/subprogram-pool`

### Query Parameters

Parameter | Description
--------- |  -----------
applianceType | Define a specific appliance type (Washer, Refrigerator, Dishwasher, Oven, Dryer ..)

<aside class="success">
Remember — You should be authenticated first!
</aside>


## Insert a new SubProgram

> The example body JSON structured like this:

```json
[
  {
    "applianceType": "Washer",
    "subprogramStrKey": "WASHER_LIQUID_DETERGENT"
  }
]

```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully inserted new subprograms",
  "data": null
}
```

This endpoint inserts new subprograms.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`POST https://procam.arcelikiot.com/api/subprogram-pool`

# Warning Pool

## Get Warning keys for a specific appliance type

> returns JSON structured like this:

```json
[
  {
    "id": 1,
    "applianceType": "Washer",
    "warningStrKey": "WASHER_WARNING_DOOR_IS_OPEN",
    "notificationInfo": {
      "strKey": "WASHER_WARNING_DOOR_IS_OPEN_NOTIFICATION",
      "priority": "HIGH",
      "necessity": "OPTON"
    }
  },
  {
    "id": 2,
    "applianceType": "Washer",
    "warningStrKey": "WASHER_WARNING_NO_WATER",
    "notificationInfo": {
      "strKey": "WASHER_WARNING_NO_WATER_NOTIFICATION",
      "priority": "HIGH",
      "necessity": "OPTON"
    }
  }
]
```

This endpoint retrieves all warnings of a specific appliance type.

### HTTP Request

`GET https://procam.arcelikiot.com/api/warning-pool`

### Query Parameters

Parameter | Description
--------- |  -----------
applianceType | Define a specific appliance type (Washer, Refrigerator, Dishwasher, Oven, Dryer ..)

<aside class="success">
Remember — You should be authenticated first!
</aside>

## Insert a new Warning

> The example body JSON structured like this:

```json
[
  {
    "applianceType": "Washer",
    "warningStrKey": "WASHER_WARNING_DOOR_IS_OPEN",
    "notificationInfo": {
      "strKey": "WASHER_WARNING_DOOR_IS_OPEN_NOTIFICATION",
      "priority": "HIGH",
      "necessity": "OPTON"
    }
  }
]

```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully inserted new warnings",
  "data": null
}
```

This endpoint inserts new warnings.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`POST https://procam.arcelikiot.com/api/warning-pool`

### Body Parameters

Parameter | Description | Options
--------- |  ----------- |  -----------
applianceType | Define a specific appliance type | Washer, Refrigerator, Dishwasher, Oven, Dryer ..
warningStrKey | Define a specific key for warning 
notificationInfo | In this block notification and priority settings will be defined
notificationInfo/strKey | Define a specific key for warning notification key
notificationInfo/priority | Define a priority for your warning | LOW, MEDIUM, HIGH, BLOCKER
notificationInfo/necessity | Define a necessity setting for your notification | OPTOFF(Optional Off), OPTON(Optional On), MANDA(Mandatory) 


# Timing Variable Pool

## Get Timing Variable keys for any appliance type

> returns JSON structured like this:

```json
[
  "TIMING_VARIABLE_REMAINING",
  "TIMING_VARIABLE_DURATION",
  "TIMING_VARIABLE_MINUTE"
]
```

This endpoint retrieves all timing variables.

### HTTP Request

`GET https://procam.arcelikiot.com/api/timing-variable-pool`

<aside class="success">
Remember — You should be authenticated first!
</aside>

## Insert a new Timing Variable

> The example body JSON structured like this:

```json
{
  "timingVariableKey": "TIMING_VARIABLE_DURATION"
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully inserted timing variables",
  "data": null
}
```

This endpoint inserts new timing variable.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`POST https://procam.arcelikiot.com/api/timing-variable-pool`

### Body Parameters

Parameter | Description
--------- |  ----------- 
timingVariableKey | Define a specific key to define timing variable



# Device States Pool

## Get Device States keys for any appliance type

> returns JSON structured like this:

```json
[
  {
    "deviceStateStrKey": "DEVICE_STATE_ON",
    "notificationInfo": {
      "strKey": "DEVICE_STATE_ON_NOTIFICATION",
      "priority": "MEDIUM"
    }
  },
  {
    "deviceStateStrKey": "DEVICE_STATE_OFF",
    "notificationInfo": {
      "strKey": "DEVICE_STATE_OFF_NOTIFICATION",
      "priority": "MEDIUM"
    }
  },
  {
    "deviceStateStrKey": "DEVICE_STATE_RUNNING",
    "notificationInfo": {
      "strKey": "DEVICE_STATE_RUNNING_NOTIFICATION",
      "priority": "MEDIUM"
    }
  }
]
```

This endpoint retrieves all device substates.

### HTTP Request

`GET https://procam.arcelikiot.com/api/device-state-pool`

<aside class="success">
Remember — You should be authenticated first!
</aside>


## Insert a Device State

> The example body JSON structured like this:

```json
{
  "deviceStateStrKey": "DEVICE_STATE_OFF",
  "notificationInfo": {
    "strKey": "DEVICE_STATE_OFF_NOTIFICATION",
    "priority": "MEDIUM"
  }
}

```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully inserted new device state",
  "data": null
}
```

This endpoint inserts new device state.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`POST https://procam.arcelikiot.com/api/device-state-pool`

### Body Parameters

Parameter | Description | Options
--------- |  ----------- |  -----------
deviceStateStrKey | Define a specific key for device state 
notificationInfo | In this block priority settings will be defined
notificationInfo/strKey | Define a specific key for warning notification key
notificationInfo/priority | Define a priority for your warning | LOW, MEDIUM, HIGH

# Device Substate Pool

## Get Device SubStates keys for any appliance type

> returns JSON structured like this:

```json
[
  {
    "applianceType": "Washer",
    "deviceSubStateStrKey": "WASHER_SUBSTATE_REMOVE_LAUNDRY",
    "notificationInfo": {
      "strKey": "WASHER_SUBSTATE_REMOVE_LAUNDRY_NOTIFICATION",
      "priority": "MEDIUM",
      "necessity": "OPTON"
    }
  },
  {
    "applianceType": "Washer",
    "deviceSubStateStrKey": "WASHER_SUBSTATE_ADD_LAUNDRY",
    "notificationInfo": {
      "strKey": "WASHER_SUBSTATE_ADD_LAUNDRY_NOTIFICATION",
      "priority": "MEDIUM"
    }
  },
  {
    "applianceType": "Washer",
    "deviceSubStateStrKey": "WASHER_SUBSTATE_RINSE_HOLD",
    "notificationInfo": {
      "strKey": "WASHER_SUBSTATE_RINSE_HOLD_NOTIFICATION",
      "priority": "MEDIUM",
      "necessity": "OPTON"
    }
  },
  {
    "applianceType": "Washer",
    "deviceSubStateStrKey": "WASHER_SUBSTATE_REMOTE_ANTICREASE",
    "notificationInfo": {
      "strKey": "WASHER_SUBSTATE_REMOTE_ANTICREASE_NOTIFICATION",
      "priority": "MEDIUM"
    }
  }
]
```

This endpoint retrieves all device substates.

### HTTP Request

`GET https://procam.arcelikiot.com/api/device-substates-pool`

<aside class="success">
Remember — You should be authenticated first!
</aside>


## Insert a Device SubState

> The example body JSON structured like this:

```json
{
    "applianceType": "Washer",
    "deviceSubStateStrKey": "WASHER_SUBSTATE_RINSE_HOLD",
    "notificationInfo": {
      "strKey": "WASHER_SUBSTATE_RINSE_HOLD_NOTIFICATION",
      "priority": "MEDIUM",
      "necessity": "OPTON"
    }
  }

```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully inserted new device substate",
  "data": null
}
```

This endpoint inserts new device state.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`POST https://procam.arcelikiot.com/api/device-state-pool`

### Query Parameters

Parameter | Description
--------- |  -----------
applianceType | Define a specific appliance type (Washer, Refrigerator, Dishwasher, Oven, Dryer ..)


### Body Parameters

Parameter | Description | Options
--------- |  ----------- |  -----------
applianceType | Define a specific appliance type | Washer, Refrigerator, Dishwasher, Oven, Dryer ..
deviceStateStrKey | Define a specific key for device substate 
notificationInfo | In this block priority settings will be defined
notificationInfo/strKey | Define a specific key for substate notification key
notificationInfo/priority | Define a priority for your substate | LOW, MEDIUM, HIGH
notificationInfo/necessity(OPTIONAL) | Define a necessity setting for your notification | OPTOFF(Optional Off), OPTON(Optional On), MANDA(Mandatory) 

# Device Settings Variable Pool

## Get Device Settings Variable keys for any appliance type

> returns JSON structured like this:

```json
[
  {
    "applianceType":"Any",
    "deviceSettingsVariableKey":"SETTINGS_VOLUME"
  }
]
```

This endpoint retrieves all timing variables.

### HTTP Request

`GET https://procam.arcelikiot.com/api/device-settings-pool`

### Query Parameters

Parameter | Description | Options
--------- |  ----------- |  ----------- 
applianceType | Define a specific appliance type or 'Any' | Any, Washer, Refrigerator, Dishwasher, Oven, Dryer ..


<aside class="success">
Remember — You should be authenticated first!
</aside>

## Insert a new Device Settings Variable

> The example body JSON structured like this:

```json
{
  "applianceType": "Washer",
  "deviceSettingsVariableKey": "SETTINGS_SOFTENER_DOSING_QUANTITY"
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully inserted device settings variable",
  "data": null
}
```

This endpoint inserts new device settings variable.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`POST https://procam.arcelikiot.com/api/device-settings-pool`

### Body Parameters

Parameter | Description | Options
--------- |  ----------- |  ----------- 
applianceType | Define a specific appliance type or 'Any' | Any, Washer, Refrigerator, Dishwasher, Oven, Dryer ..
deviceSettingsVariableKey | Define a specific key to define device settings variable

# Functional Configuration

## Create a new Functional Configuration

> The example body JSON structured like this:

```json
{
  "programsIndex": 36,
  "subprogramIndex": 37,
  "deviceStatesReadIndex": 35,
  "deviceStatesWriteIndex": 34,
  "deviceSubStatesIndex": 50,
  "settingsIndex": 38,
  "warningsIndex": 56
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully inserted device settings variable",
  "data": {
    "functionalConfigurationId": 13
  }
}
```

> This API call initilize a empty functional configuration

This endpoint inserts new functional configurations.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`POST https://procam.arcelikiot.com/api/functional-configuration`

### Body Parameters

All indexes show the index of variable in the wifi array.

## Update Program Values

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "values": [
    {
      "strKey": "PROGRAM_COTTONS",
      "value": 1
    },
    {
      "strKey": "PROGRAM_DARKWASH",
      "value": 2
    },
    {
      "strKey": "PROGRAM_RINSING",
      "value": 3
    },
    {
      "strKey": "PROGRAM_CURTAIN",
      "value": 4,
      "isDownloadCycleProgram": true
    }
  ]
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's programs",
  "data": null
}
```

This API call update configuration's programs

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/programs`

## Update SubProgram Values

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "values": [
    {
      "subprogramKey": "WASHER_TEMPERATURE",
      "index": 37,
      "enumValues": [
        {
         "strKey": "TEMPERATURE_COLD_WASH",
         "wifiArrayValue": 0
        }
      ],
      "boundedValues": [
        {
          "strKey": "TEMPERATURE",
          "lowerLimit": 20,
          "upperLimit": 90,
          "step": 10,
          "factor": 1,
          "unit": "C"
        }
      ]
    },
    {
      "subprogramKey": "WASHER_SPIN",
      "index": 38,
      "enumValues": [
        {
        "strKey": "SPIN_NO_SPIN",
        "wifiArrayValue": 0
        },
        {
         "strKey": "SPIN_RINSE_HOLD",
         "wifiArrayValue": 17
        }
      ],
      "boundedValues": [
        {
          "strKey": "SPIN",
          "lowerLimit": 400,
          "upperLimit": 1400,
          "step": 200,
          "factor": 100,
          "unit": ""
        }
      ]
    },
    {
      "subprogramKey": "WASHER_PHR",
      "index": 65,
      "isSwitch": 1,
      "enumValues": [
        {
          "strKey": "WASHER_PHR_OFF",
          "wifiArrayValue": 0
        },
        {
          "strKey": "WASHER_PHR_ON",
          "wifiArrayValue": 1
        }
      ]
    }
  ]
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's subprograms",
  "data": null
}
```

This API call update configuration's subprograms

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/subprograms`


You need to address the functional configuration id. Then you have to specify the subprograms you want to add in "values" section.

For each subprogram section in values section, you need to specify some elements

Parameter | Description
--------- |  -----------
strKey | Address some subprogram key from subprogram pool
index | Specifies the index at wifi array
enumValues| specifies the enumerated values of a subprogram
boundedValues| specifies the values between a certain range
isSwitch | for the subprograms that includes only two enum values, indicate that whether it will be shown as swicth or not
excludesSubprograms | array of a subprogram keys that will be excluded


## Update Warning Values

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "values": [
    {
      "warningKey": "DISHWASHER_WARNING_NO_RINSE_AID",
      "bitIndex": 0
    },
    {
      "warningKey": "DISHWASHER_WARNING_NO_WATER",
      "bitIndex": 1
    }
  ]
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's warnings",
  "data": null
}
```

This API call update configuration's subprograms

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/warnings`


## Update Timing Variable Values

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "values":[
    {
      "timingVariableKey": "TIMING_VARIABLE_REMAINING",
      "hourIndex":45,
      "minuteIndex":46
    },
    {
      "timingVariableKey": "TIMING_VARIABLE_DELAY",
      "hourIndex":47,
      "minuteIndex":48
    },
    {
      "timingVariableKey": "TIMING_VARIABLE_DURATION",
      "hourIndex":49,
      "minuteIndex":50
    }
  ]
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's warnings",
  "data": null
}
```

This API call update configuration's settings

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/timing-variables`


## Update Settings Values

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "values":[
    {
      "settingKey": "SETTINGS_SOFTENER_DOSING_QUANTITY",
      "index": 68,
      "enumValues": [
        {
          "strKey": "QUANTITY_LOW",
          "wifiArrayValue": 0
        },
        {
          "strKey": "QUANTITY_MEDIUM",
          "wifiArrayValue": 1
        },
        {
          "strKey": "QUANTITY_HIGH",
          "wifiArrayValue": 2
        }
      ]
    },
    {
      "settingKey": "SETTING_DETERGENT_TYPE",
      "index": 65,
      "enumValues": [
        {
          "strKey": "SETTING_DETERGENT_TYPE_POWDER",
          "wifiArrayValue": 0
        },
        {
          "strKey": "SETTING_DETERGENT_TYPE_TABLET",
          "wifiArrayValue": 1
        }
      ]
    }
  ]
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's warnings",
  "data": null
}
```

This API call update configuration's settings

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/settings`


## Update Device State Values

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "values":[
    {
      "stateKey": "DEVICE_STATE_ON",
      "value": 10
    },
    {
      "stateKey": "DEVICE_STATE_OFF",
      "value": 20
    },
    {
      "stateKey": "DEVICE_STATE_RUNNING",
      "value": 30
    },
    {
      "stateKey": "DEVICE_STATE_TIME_DELAY_ACTIVE",
      "value": 40
    }
  ]
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's device states",
  "data": null
}
```

This API call update configuration's device states

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/device-states`

## Update Device SubState Values

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "values":[
    {
      "stateKey": "WASHER_SUBSTATE_WASHING",
      "value": 1
    },
    {
      "stateKey": "WASHER_SUBSTATE_SPIN",
      "value": 2
    },
    {
      "stateKey": "WASHER_SUBSTATE_PREWASH",
      "value": 3
    }
  ]
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's device substates",
  "data": null
}
```

This API call update configuration's device states

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/device-substates`


## Update Program Options

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "disabledOptions":[
    {
      "programKey": "PROGRAM_COTTONS_ECO",
      "options":[
        "WASHER_PHR",
        "WASHER_FAST_PLUS",
        "WASHER_HIDDEN_ANTI_CREASE"
      ]
    },
    {
      "programKey": "PROGRAM_SYNTHETICS",
      "options":[
        "WASHER_PHR"
      ]
    }
  ],
  "optionOverrides":[
    {
      "programKey": "PROGRAM_SYNTHETICS",
      "overrides":[
        {
          "subprogramKeyRef": "WASHER_TEMPERATURE",
          "allowedValueIndices": [
            0,
            1,
            2,
            3,
            4,
            5
          ]
        },
        {
          "subprogramKeyRef": "WASHER_SPIN",
          "allowedValueIndices": [
            0,
            1,
            2,
            3,
            4,
            5,
            6
          ]
        }
      ]
    }
  ]
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's program options",
  "data": null
}
```

This API call update configuration's program options

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/program-options`

## Update Download Cycle

> The example body JSON structured like this:

```json
{
  "functionalConfigurationId": 13,
  "index":71
}
```

> The above body returns JSON structured like this:

```json
{
  "success": true,
  "code": "200",
  "description": "Succesfully updated configuration's download cycle",
  "data": null
}
```

This API call update configuration's download cycle

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`PUT https://procam.arcelikiot.com/api/functional-configuration/download-cycle`