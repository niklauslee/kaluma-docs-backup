# UART

The `uart` module supports communication with computers or devices using serial ports \(UART\). Use `require('uart')` to access this module.

## Class: UART

An instances of `UART` represents a UART port.

### UART.PARITY\_NONE

* `<number>` = `0`.

Do not use a parity bit.

### UART.PARITY\_ODD

* `<number>` = `1`.

Use odd parity bit

### UART.PARITY\_EVEN

* `<number>` = `2`.

Use even parity bit

### UART.FLOW\_NONE

* `<number>` = `0`.

Do not use flow control.

### UART.FLOW\_RTS

* `<number>` = `1`.

Use RTS flow control.

### UART.FLOW\_CTS

* `<number>` = `2`.

Use CTS flow control.

### UART.FLOW\_RTS\_CTS

* `<number>` = `3`.

Use both RTS and CTS flow control.

### new UART\(port\[, options\]\)

* **`port`** `<number>` UART port number. This value should be less than board.NUM\_UART.
* **`options`** `<object>` The object of UART options. _Default values are depends on board \(Check in a board page\)._
  * **`baudrate`** `<number>` Baud rate. One of the `[0, 50, 75, 110, 134, 150, 200, 300, 600, 1200, 1800, 2400, 4800, 9600, 19200, 38400, 57600, 115200, 230400]`. **Default:** `9600`
  * **`bits`** `<number>` Number of bits per a character. One of the `[8, 9]`. **Default:**`8`
  * **`parity`** `<number>`. The parity is one of the `UART.PARITY_NONE (0)`, `UART.PARITY_ODD (1)`, or `UART.PARITY_EVEN (2)`. **Default:** `UART.PARITY_NONE`.
  * **`stop`** `<number>` Number of stop bits. One of the `[1, 2]`. **Default:** `1`.
  * **`flow`** `<number>` Flow control. One of the `UART.FLOW_NONE (0)`, `UART.FLOW_RTS (1)`, `UART.FLOW_CTS (2)`, or `UART.FLOW_RTS_CTS (3)`. **Default:** `UART.FLOW_NONE`
  * **`bufferSize`** `<number>` The size of internal read buffer. **Default:** `1024`.
  * **`tx`** `<number>` UART TX pin number.
  * **`rx`** `<number>` UART RX pin number.
  * **`dataEvent`** `<string|number>` A condition when the `data` event is emitted. if the type of this value is &lt;number&gt;, `data` event is emitted when the number of characters are received. if the type of this value is &lt;string&gt;, `data` event is emitted when that specific character is received. **Default:**`undefined`.

```javascript
// Javascript example: Create the UART instance and close it 
var UART = require('uart').UART;
var options = {
  baudrate: 9600,
  bits: 8,
  partity: UART.PARTIY_NONE,
  stop: 1,
  flow: UART.FLOW_NONE,
  bufferSize: 2048
};
var serial0 = new UART(0, options);
// read or write data...
serial0.close();
```

### write\(data\[, options\]\)

* **`data`** `<Uint8Array|string>` Data to write.
* **`options`** `<object>` 
  * **`count`** `<number>` Indicates how many times to write data. **Default:** `1`.

Writes data to the UART port.

```javascript
var UART = require('uart').UART;
var serial0 = new UART(0, {baudrate: 38400});

// Write a string
serial0.write('Hello, world\n');

// Write Uint8Array
serial0.write(new Uint8Array([0x00, 0x7f, 0x80, 0xff]));

serial0.close();
```

### close\(\)

Close the UART port.

### Event: 'data'

* **`data`** `<Uint8Array>` Received data.

The `data` event is emitted whenever data is arrived \(buffer size may varies\).

If the `dataEvent` option is given with a character \(e.g. `'\n'`\), this event is emitted whenever the given character has arrived. If the character is not arrived until the buffer is full, you will lose the data in the buffer.

If the `dataEvent` option is given with a number \(e.g. `10`\), this event is emitted whenever buffer length has reached to the given number. The number should be less than the buffer size.

```javascript
// The data is shown when '\n' character is received.
var UART = require('uart').UART;

var options = {
  baudrate: 9600,
  dataEvent: '\n'
};

var serial0 = new UART(0, options);

// The `data` event is emitted whenever '\n' is received.
serial0.on('data', function (data) {
  var str = String.fromCharCode.apply(null, data);
  console.log(str);
});
```

```javascript
var UART = require('uart').UART;
var serial0 = new UART(0);

serial0.on('data', function (data) {
  var str = String.fromCharCode.apply(null, data);
  print(ch);
});
```

