# Marantz AV Receiver Control
This library allows you to control the basic functions of a Marantz Receiver using io.js/node.js. This library is just a wrapper around the Marantz HTTP 'API'. However it handles a few things like:

* Rate limiting API calls - the receiver, at least in my testing would fail if you made too many requests at once.
* Normalizing their horrible naming conventions

> Note, that I used a few ES6 functions that are compatible with iojs in this library so you will either need to enable the flags or edit the library and use a polyfill if you are using Node.js.


## Install

```
npm install marantz-avr
```

## Usage

### setPowerState

Turns the receiver on/off

```js
let AVReceiver = require('marantz-avr');
let receiver = new AVReceiver('ip_address');

// True turns the receiver on / false off
receiver.setPowerState(true).then(
    res => console.log(res), 
    error => console.log(error)
);
```

### getState

Returns the state of the receiver

```
receiver.getState().then(
    res => console.log(res), 
    error => console.log(error)
);
```

```
{
  power: true,
  input: 'GAME',
  volumeLevel: '-33.0',
  mute: false,
  surroundMode: 'DIRECT' 
}
```

