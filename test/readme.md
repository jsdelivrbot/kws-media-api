KWS Media API - Tests
=====================
Tests are autonomous, only requirement is to exec previously ```npm install```
to have installed all the dev dependencies.

## Environments

### Browser

To exec tests in browser, you need to build the browser version of the library
with ```node_modules/.bin/grunt```.

After that, just open the file ```test/index.html``` with any browser, and the
tests will launch automatically using [QUnit]. In case of the browser raising
security policy errors, you can host the code using any static web server from
the source code root folder, for example using the command
```python -m SimpleHTTPServer 8000```.

You can be able to configure to what WebSocket endpoint you want to connect on
the dropdown at the top of the tests page.

### Node.js

To exec test in Node.js, you only need to exec ```npm test``` that will launch
all the tests automatically using [QUnit-cli].

If you need to use a WebSocket endpoint different from the default one, you can exec the underlying test command with
```node_modules/.bin/qunit-cli -c kwsMediaApi:. -c wock:node_modules/wock -c test/_common.js -c test/_proxy.js test/*.js``` and append the *ws_uri* parameter.


# BasicPipeline

## Creation

A basic pipeline reading a video from its URL and stream it over HTTP without
any filters.

### Assertions

* player endpoint is set
* HttpGet endpoint is set
* pipeline URL is set


# FaceOverlayFilter

## Detect face in a video

Play a video setting a face overlay and capture an End of Stream event

### Assertions

* player endpoint is set
* FaceOverlay filter is set
* End of Stream event is received


# GStreamerFilter

## End of Stream

Play a video using an ad-hoc GStreamer filter and capture an End of Stream event

### Assertions

* player endpoint is set
* GStreamer filter is set
* connection of elements was successful
* End of Stream event is received


# HttpGetEndpoint

## Method GetUrl

Create an empty HttpGet endpoint and check it has a valid URL

### Assertions

* HttpGet endpoint is set
* HttpGet endpoint has a valid URL


## Media session started

Create an empty HttpGet endpoint and check it has a valid URL

### Assertions

* player endpoint is set
* HttpGet endpoint is set
* HttpGet endpoint has a valid URL
* MediaSessionStarted event is dispatched
* End of Stream event is dispatched


# PlateDetectorFilter

## Detect plate in a video

Check if a plate is detected on a video

### Assertions

* a plate detected event is dispatched


