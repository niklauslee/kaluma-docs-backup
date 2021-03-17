# AT Command

The `at` module supports sending AT commands and handling the responses. This module is useful for the devices controlled by AT command such as Wi-Fi, GSM, Bluetooth modules. Use `require('at')` to access this module.

## Class: ATCommand

An instances of `ATCommand` represents a AT command handler. This class is a subclass of [`EventEmitter`](events.md).

### new ATCommand\(uart\[, options\]\)

* **`uart`** `{UART}` UART object where a device is connected which controlled by AT command.
* **`options`** `{object}` 
  * **`debug`** `{boolean}` Print all data received from UART if `true`.

Create a AT command handler.

> Note that data received from `uart` is converted to an ASCII string \(1 byte to 1 char\) for easy manipulation.

### at.send\(cmd\[, callback\[, match\[, options\]\]\)

* **`cmd`** `{string|Uint8Array}` AT command \(or data\) to send. If `Uint8Array` type is given, it send as data.
* **`callback`** `{Function}` Callback called when expected response is arrived.
  * **`result`** `{string}` Result status. One of array items of `match` parameter or `'TIMEOUT'`.
  * **`response`** `{string}` Response data.
* **`match`** `{Array<string>|Function|number)}` Indicates what is expected response of the AT command. **Default:** `['OK', 'ERROR', 'FAIL']`
* **`options`** `{object}`
  * **`timeout`** `{number}` Timeout for waiting response. **Default:** `10000` \(10 sec\). When timeout, callback is called with `'TIMEOUT'` for the second parameter.
  * **`prepend`** `{boolean}` Process this command prior to all other commands in the queue. **Default:** `false`.
  * **`clean`** `{boolean}` Clear the response buffer before sending the AT command. **Default:** `false`.
  * **`sendAsData`** `{boolean}` If `true`, `cmd` is sent as data without appending `'\r\n'` in the end. **Default:** `false`.

Sends AT command and wait for expected response. If you didn't provide parameters other than `cmd`, it sends AT command and then process the next command in the queue without waiting for expected response.

```javascript
at.send('AT+XXX'); // send AT command and do not wait for response
```

If you need to get response, provide `callback` and `match` parameters. If a number is given for `match` parameter, `callback` is called with the response just after waiting response for the given number of time \(milliseconds\).

```javascript
at.send('AT+XXX', function (result, response) {
  console.log(response);
}, 1000); // wait 1 sec for response
```

If an array of string is given for the `match` parameter, `callback` is called with the response and the matched item in the `match` parameter when there is a line matched with the `match` parameter in the response buffer.

```javascript
at.send('AT+XXX', function (result, response) {
  if (result === 'OK') {
    console.log(response);
  } else {
    console.error('ERROR');
  }
}, ['OK', 'ERROR', 'FAIL']);
```

If you cannot specify the what is the expected response with the wait time or match strings, you can provide a function for the `match` parameter. The match function should return a number indicating position of the next character of expected response in the response buffer. When the match function returns greater than zero, `callback` is called with the response \(`at.buffer[0..n-1]`\). The remained response \(`at.buffer[n..]`\) data may be handled with the next AT command.

```javascript
at.send('AT+XXX', function (result, response) {
  console.log(response);
}, function (buffer) {
  var idx = buffer.indexOf('\r\nOK\r\n');
  if (idx > -1) {
    return idx + 6; // position to the next char of '\r\nOK\r\n'
  } else {
    return -1;
  }
});
```

### at.addLineHandler\(match, handler\)

* **`match`** `{string}` A match string.
* **`handler`** `{Function}` Handler function.
  * `line` `{string}`

Add a line handler. If there is a line starts with the `match` parameter in the response buffer, the handler function will be called. The data from start to the matched line are removed from the response buffer.

```javascript
at.addLineHandler('WIFI DISCONNECTED', (line) => {
  console.log('Wifi disconnected');
});
```

### at.removeLineHandler\(match\)

* **`match`** `{string}` 

Remove a line handler.

```javascript
at.addLineHandler('WIFI DISCONNECTED', (line) => {
  console.log('Wifi disconnected');
});

at.removeLineHandler('WIFI DISCONNECTED');
```

### at.addResponseHandler\(handler\)

* **`handler`** `{Function}` Response handler function.
  * **`buffer`** `{string}` 

Add a response handler. If line handlers are not enough to handle response, you can use response handlers. The response handler function should return remained response buffer after removing handled data.

```javascript
// Handle +IPD response of ESP8266
// e.g.) "+IPD,11:Hello,World"
at.addResponseHandler((buffer) => {
  if (buffer.startsWith('+IPD,')) {
    var p = buffer.indexOf(':');
    if (p > -1) {
      var len = buffer.substr(5, p - 5); // length of IPD data
      if (buffer.length > p + len) { // all data received
        var res = buffer.substr(p + 1, parseInt(len));
        console.log('Data received: ', res); // Handle response
        var remain = buffer.substr(p + 1 + len);
        return remain; // return unhandled response
      }
    }
  }
  return buffer; // skip response handling
});
```

### at.removeResponseHandler\(handler\)

* **`handler`** `{Function}` Response handler function.

Remove a response handler.

### at.pause\(\)

Pause to process handling response buffer. Any data in the response buffer will not be handled \(deleted\), but received data from UART will be accumulated to the response buffer.

### at.resume\(\)

Resume to process handling response buffer.

### at.processLineHandlers\(\)

Enforce to process line handlers.

### at.processResponseHandlers\(\)

Enforce to process response handlers.

### at.buffer

* `{string}`

Response buffer for the responses of AT commands.



