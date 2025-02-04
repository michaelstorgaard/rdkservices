<!-- Generated automatically, DO NOT EDIT! -->
<a name="head.Linear_Playback_Control_Plugin"></a>
# Linear Playback Control Plugin

**Version: 1.0**

**Status: :black_circle::white_circle::white_circle:**

LinearPlaybackControl plugin for Thunder framework.

### Table of Contents

- [Introduction](#head.Introduction)
- [Configuration](#head.Configuration)
- [Properties](#head.Properties)
- [Notifications](#head.Notifications)

<a name="head.Introduction"></a>
# Introduction

<a name="head.Scope"></a>
## Scope

This document describes purpose and functionality of the LinearPlaybackControl plugin. It includes detailed specification of its configuration, properties provided and notifications sent.

<a name="head.Case_Sensitivity"></a>
## Case Sensitivity

All identifiers on the interface described in this document are case-sensitive. Thus, unless stated otherwise, all keywords, entities, properties, relations and actions should be treated as such.

<a name="head.Acronyms,_Abbreviations_and_Terms"></a>
## Acronyms, Abbreviations and Terms

The table below provides and overview of acronyms used in this document and their definitions.

| Acronym | Description |
| :-------- | :-------- |
| <a name="acronym.API">API</a> | Application Programming Interface |
| <a name="acronym.HTTP">HTTP</a> | Hypertext Transfer Protocol |
| <a name="acronym.JSON">JSON</a> | JavaScript Object Notation; a data interchange format |
| <a name="acronym.JSON-RPC">JSON-RPC</a> | A remote procedure call protocol encoded in JSON |

The table below provides and overview of terms and abbreviations used in this document and their definitions.

| Term | Description |
| :-------- | :-------- |
| <a name="term.callsign">callsign</a> | The name given to an instance of a plugin. One plugin can be instantiated multiple times, but each instance the instance name, callsign, must be unique. |

<a name="head.References"></a>
## References

| Ref ID | Description |
| :-------- | :-------- |
| <a name="ref.HTTP">[HTTP](http://www.w3.org/Protocols)</a> | HTTP specification |
| <a name="ref.JSON-RPC">[JSON-RPC](https://www.jsonrpc.org/specification)</a> | JSON-RPC 2.0 specification |
| <a name="ref.JSON">[JSON](http://www.json.org/)</a> | JSON specification |
| <a name="ref.Thunder">[Thunder](https://github.com/WebPlatformForEmbedded/Thunder/blob/master/doc/WPE%20-%20API%20-%20WPEFramework.docx)</a> | Thunder API Reference |

<a name="head.Configuration"></a>
# Configuration

The table below lists configuration options of the plugin.

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| callsign | string | Plugin instance name (default: *LinearPlaybackControl*) |
| classname | string | Class name: *LinearPlaybackControl* |
| locator | string | Library name: *libWPEFrameworkLinearPlaybackControl.so* |
| autostart | boolean | Determines if the plugin is to be started automatically along with the framework |

<a name="head.Properties"></a>
# Properties

The following properties are provided by the LinearPlaybackControl plugin:

LinearPlaybackControl interface properties:

| Property | Description |
| :-------- | :-------- |
| [channel](#property.channel) | Current channel |
| [seek](#property.seek) | TSB seek position offset, from live position, in seconds |
| [trickPlay](#property.trickPlay) | Trick play speed and direction |
| [status](#property.status) <sup>RO</sup> | Current TSB status information containing buffer size, seek position and health status |
| [tracing](#property.tracing) | Tracing enable/disable flag |

<a name="property.channel"></a>
## *channel <sup>property</sup>*

Provides access to the current channel.

### Value

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| (property) | object | Current channel |
| (property).channel | string | Channel address |

> The *muxid* shall be passed as the index to the property, e.g. *LinearPlaybackControl.1.channel@0*.

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 30 | ```ERROR_BAD_REQUEST``` | Bad JSON param data format. |
| 39 | ```ERROR_READ_ERROR``` | Error reading file or parsing one or more values. |
| 40 | ```ERROR_WRITE_ERROR``` | Error writing to file. |

### Example

#### Get Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.channel@0"
}
```
#### Get Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "channel": "chan_select"
    }
}
```
#### Set Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.channel@0",
    "params": {
        "channel": "chan_select"
    }
}
```
#### Set Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": "null"
}
```
<a name="property.seek"></a>
## *seek <sup>property</sup>*

Provides access to the TSB seek position offset, from live position, in seconds.

### Value

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| (property) | object | TSB seek position offset, from live position, in seconds |
| (property).seekPosInSeconds | number | TSB seek position offset from live in seconds. The value must be an unsigned integer. If the value exceeds the current TSB size, the seek position will be reduced accordingly |

> The *muxid* shall be passed as the index to the property, e.g. *LinearPlaybackControl.1.seek@0*.

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 30 | ```ERROR_BAD_REQUEST``` | Bad JSON param data format. |
| 39 | ```ERROR_READ_ERROR``` | Error reading file or parsing one or more values. |
| 40 | ```ERROR_WRITE_ERROR``` | Error writing to file. |

### Example

#### Get Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.seek@0"
}
```
#### Get Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "seekPosInSeconds": 0
    }
}
```
#### Set Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.seek@0",
    "params": {
        "seekPosInSeconds": 0
    }
}
```
#### Set Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": "null"
}
```
<a name="property.trickplay"></a>
## *trickplay <sup>property</sup>*

Provides access to the trick play speed and direction.

### Value

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| (property) | object | Trick play speed and direction |
| (property).speed | number | Trick play speed. The direction is defined by the sign of speed, where a negative value means rewind and positive value means fast forward |

> The *muxid* shall be passed as the index to the property, e.g. *LinearPlaybackControl.1.trickplay@0*.

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 30 | ```ERROR_BAD_REQUEST``` | Bad JSON param data format. |
| 39 | ```ERROR_READ_ERROR``` | Error reading file or parsing one or more values. |
| 40 | ```ERROR_WRITE_ERROR``` | Error writing to file. |

### Example

#### Get Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.trickplay@0"
}
```
#### Get Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "speed": -4
    }
}
```
#### Set Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.trickplay@0",
    "params": {
        "speed": -4
    }
}
```
#### Set Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": "null"
}
```
<a name="property.status"></a>
## *status <sup>property</sup>*

Provides access to the current TSB status information containing buffer size, seek position and health status.

> This property is **read-only**.

### Value

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| (property) | object | Current TSB status information containing buffer size, seek position and health status |
| (property).maxSizeInBytes | number | Maximum TSB size in bytes |
| (property).currentSizeInBytes | number | Current TSB size in bytes |
| (property).currentSizeInSeconds | number | Current TSB size in seconds |
| (property).seekPosInBytes | number | Current TSB seek position offset from live in bytes. The value is an unsigned integer and cannot exceed the current TSB size in bytes |
| (property).seekPosInSeconds | number | Current TSB seek position offset from live in seconds. The value is an unsigned integer and cannot exceed the current TSB size in seconds |
| (property).trickPlaySpeed | number | Current trick play speed and direction. The direction is defined by the sign of speed, where a negative value means rewind and positive value means fast forward |
| (property).streamSourceLost | boolean | Boolean indicating if the buffer source is lost (true) as a result of e.g. network connectivity issues or not (false) |
| (property).streamSourceLossCount | number | Number of times the streaming is lost and the TSB stopped receiving data from the stream source, during a valid channel selected |

> The *muxid* shall be passed as the index to the property, e.g. *LinearPlaybackControl.1.status@0*.

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 39 | ```ERROR_READ_ERROR``` | Error reading file or parsing one or more values. |

### Example

#### Get Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.status@0"
}
```
#### Get Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "maxSizeInBytes": 0,
        "currentSizeInBytes": 0,
        "currentSizeInSeconds": 0,
        "seekPosInBytes": 0,
        "seekPosInSeconds": 0,
        "trickPlaySpeed": -4,
        "streamSourceLost": false,
        "streamSourceLossCount": 0
    }
}
```
<a name="property.tracing"></a>
## *tracing <sup>property</sup>*

Provides access to the tracing enable/disable flag.

### Value

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| (property) | object | Tracing enable/disable flag |
| (property).tracing | boolean | Tracing enable (true) / disable (false) |

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 1 | ```ERROR_GENERAL``` | General failure. |
| 30 | ```ERROR_BAD_REQUEST``` | Bad JSON param data format. |

### Example

#### Get Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.tracing"
}
```
#### Get Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "tracing": true
    }
}
```
#### Set Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "LinearPlaybackControl.1.tracing",
    "params": {
        "tracing": true
    }
}
```
#### Set Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": "null"
}
```
<a name="head.Notifications"></a>
# Notifications

Notifications are autonomous events, triggered by the internals of the implementation, and broadcasted via JSON-RPC to all registered observers.Refer to [[Thunder](#ref.Thunder)] for information on how to register for a notification.

The following events are provided by the LinearPlaybackControl plugin:

LinearPlaybackControl interface events:

| Event | Description |
| :-------- | :-------- |
| [speedchanged](#event.speedchanged) | Indicates that the trick play speed has changed |

<a name="event.speedchanged"></a>
## *speedchanged <sup>event</sup>*

Indicates that the trick play speed has changed.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.speed | number | New trick play speed. The direction is defined by the sign of speed, where a negative value means rewind and positive value means fast forward |
| params.muxId | number | Stream muxId |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.speedchanged",
    "params": {
        "speed": -4,
        "muxId": 0
    }
}
```
