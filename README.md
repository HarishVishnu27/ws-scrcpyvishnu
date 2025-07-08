# ws-scrcpyvishnu

iOS-only web client for device streaming and control.

## Requirements

Browser must support the following technologies:
* WebSockets
* MJPEG display

Server:
* Node.js v10+
* node-gyp ([installation](https://github.com/nodejs/node-gyp#installation))

Device:
* iOS device with [WebDriverAgent][WebDriverAgent] configured
* [ws-qvh][ws-qvh] installed for streaming (optional)

## Build and Start

Make sure you have installed [node.js](https://nodejs.org/en/download/),
[node-gyp](https://github.com/nodejs/node-gyp) and
[build tools](https://github.com/nodejs/node-gyp#installation)
```shell
git clone https://github.com/HarishVishnu27/ws-scrcpyvishnu.git
cd ws-scrcpyvishnu

npm install
npm start
```

## Supported features

### iOS

#### Screen Casting

Requires [ws-qvh][ws-qvh] available in `PATH`.

#### MJPEG Server

MJPEG server is enabled by default in the build configuration.

Alternative way to stream screen content. It does not
require additional software as `ws-qvh`, but may require more resources as each
frame encoded as jpeg image.

#### Remote control

To control device we use [appium/WebDriverAgent][WebDriverAgent].
Functionality limited to:
* Simple touch
* Scroll
* Home button click

Make sure you did properly [setup WebDriverAgent](https://appium.io/docs/en/drivers/ios-xcuitest-real-devices/).
WebDriverAgent project is located under `node_modules/appium-webdriveragent/`.

You might want to enable `AssistiveTouch` on your device: `Settings/General/Accessibility`.

## Custom Build

This project is configured for iOS-only functionality. You can customize the build by overriding the
[default configuration](/webpack/default.build.config.json) in
[build.config.override.json](/build.config.override.json):

* `INCLUDE_APPL` - include code for iOS device tracking and control (enabled by default)
* `USE_WDA_MJPEG_SERVER` - configure WebDriverAgent to start MJPEG server (enabled by default)
* `USE_QVH_SERVER` - include support for [ws-qvh][ws-qvh] streaming (enabled by default)
* `PATHNAME` - web server pathname (default: "/")

## Run configuration

You can specify a path to a configuration file in `WS_SCRCPY_CONFIG`
environment variable.

If you want to have another pathname than "/" you can specify it in the
`WS_SCRCPY_PATHNAME` environment variable.

Configuration file format: [Configuration.d.ts](/src/types/Configuration.d.ts).

Configuration file example: [config.example.yaml](/config.example.yaml).

## Known issues

* On Safari file upload does not show progress (it works in one piece).
* WebDriverAgent may require manual setup and certificate provisioning for iOS devices.

[scrcpy]: https://github.com/Genymobile/scrcpy
[scrcpy]: https://github.com/Genymobile/scrcpy
[fork]: https://github.com/NetrisTV/scrcpy
[ws-qvh]: https://github.com/NetrisTV/ws-qvh
[WebDriverAgent]: https://github.com/appium/WebDriverAgent
