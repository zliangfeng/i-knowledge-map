# internet of things

## Refs

- [Talk to your Serial devices(NodeJS 技术栈访问 USB 接口实现跨设备通讯？)](https://serialport.io)

## Examples

```js
const SerialPort = require('serialport')
const port = new SerialPort('/dev/tty-usbserial1', function (err) {
  if (err) {
    return console.log('Error: ', err.message)
  }
})

port.write('main screen turn on', function(err) {
  if (err) {
    return console.log('Error on write: ', err.message)
  }
  console.log('message written')
})

// Read data that is available but keep the stream in "paused mode"
port.on('readable', function () {
  console.log('Data:', port.read())
})

// Switches the port into "flowing mode"
port.on('data', function (data) {
  console.log('Data:', data)
})

// Pipe the data into another stream (like a parser or standard out)
const lineStream = port.pipe(new Readline())
```
