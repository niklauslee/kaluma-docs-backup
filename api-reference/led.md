# LED

The `led` module supports LED which connect to GPIO pins. Use `require('led')` to access this module.

## Class: LED

An instances of `LED` represents a LED.

### new LED\(pin\)

* **`pin`** `<number>` Pin number where LED connected.

```javascript
// Javascript example: Create the LED instance 
var LED = require('led').LED;
var led = new LED(20); // LED connected to pin 20.

// Using the board object.
var led = board.led(0); // LED connected to pin 0.
var ledOnBoard = board.LED0; //on-board LED0.
```

### on\(\)

Turns on the LED.

```javascript
// Javascript example: Turn on the LED.
var led = board.led(20); // LED connected to pin 20.
led.on();
```

### off\(\)

Turns off the LED.

```javascript
// Javascript example: Turn off the LED.
var LED = require('led').LED;
var led = new LED(20); // LED connected to pin 20.
led.off();
```

### toggle\(\)

This method toggles the LED.

```javascript
// Javascript example: Toggle the LED.
var led = board.led(0); // LED connected to pin 0.
led.on();
delay(1000); // wait for 1sec
led.off();
delay(1000); // wait for 1sec
led.toggle(); // on
delay(1000); // wait for 1sec
led.toggle(); // off
```

### read\(\)

* Returns: `<number>` State of the LED. 1 means LED ON and 0 means LED OFF state.

Read the state of the LED.

```javascript
// Javascript example: Read the state of LED.
var led = board.led(20); // LED connected to pin 20.
led.on();
console.log(led.read()); // Returns 1.
delay(1000);
led.off();
console.log(led.read()); // Returns 0.
```

### pin

* `<number>`

Pin number of the LED.

```javascript
// Javascript example: Print out the LED pin number.
var LED = require('led').LED;
var led = new LED(20); // LED connected to pin 20.
console.log (led.pin); // print out the LED pin number, 20;
```

