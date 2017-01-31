# react-native-tvos-controller
TvOS remote controller module for react native.
Including "tap","long press","swipe" and "pan" gesture.
[React Native for TVOS](https://medium.com/@7ynk3r/react-native-apple-tv-today-48beb398a1ab#.5pp5drlyy)
[react-native-tvos-controller demo video](https://youtu.be/pou8ffWY8EY)

## Install

```shell
npm install --save react-native-tvos-controller
```

## Automatically link

#### With React Native 0.27+

```shell
react-native link react-native-tvos-controller
```

#### With older versions of React Native

You need [`rnpm`](https://github.com/rnpm/rnpm) (`npm install -g rnpm`)

```shell
rnpm link react-native-tvos-controller
```

##Usage

```javascript
import reactNativeTvosController from "react-native-tvos-controller;
```

###connect###

```javascript
reactNativeTvosController.connect()
```
Connect the remote controller of apple TV.

###enablePanGesture###

```javascript
reactNativeTvosController.enablePanGesture();
```
You will receive the specific moving offset tracing data if you enable the pan gesture.
You can't receive the swipe event anymore.

###disablePanGesture###

```javascript
reactNativeTvosController.disablePanGesture();
```
You won't receive the specific moving offset tracing data if you disable the pan gesture.
You can continue receiving the swipe event.

###subscribe###

Subscribe the native events of Apple's remote controller.

####events####

#####TAP#####

```javascript
var tapSubscription = reactNativeTvosController.subscribe('TAP',
    (e) => {
      console.log("tapped");
      console.log(JSON.stringify(e));
      /*
      e.type : "PlayPause" || "Menu" || "Select" || "UpArrow" || "DownArrow" || "LeftArrow" || "RightArrow"
      e.code : 0 || 1 || 2 || 3 || 4 || 5 || 6
      */
    });
```

#####SWIPE#####

```javascript
var swipeSubscription = reactNativeTvosController.subscribe('SWIPE',
    (e) => {
      console.log("swiped");
      console.log(JSON.stringify(e));
      /*
      e.direction : "Right" || "Down" || "Left" || "Up"
      e.code : 0 || 1 || 2 || 3 
      */
    });
```

#####LONGPRESS#####

```javascript
var longPressSubscription = reactNativeTvosController.subscribe('LONGPRESS',
    (e) => {
      console.log("longPressed");
      console.log(JSON.stringify(e));
      /*
      e.state : "Began" || "Ended"
      e.code : 0 || 1
      */
    });
```

#####PAN#####

```javascript
var panSubscription = reactNativeTvosController.subscribe('PAN',
    (e) => {
      console.log("panned");
      console.log(JSON.stringify(e));
      /*
      e.state : "Changed"
      e.x : (x offset)
      e.y : (y offset)
      */
    });
```















