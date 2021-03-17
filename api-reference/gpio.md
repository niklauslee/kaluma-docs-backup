# GPIO

The `gpio` module supports GPIO pin abstraction. Use `require('gpio')` to access this module.

## Class: GPIO

An instances of `GPIO` represents a GPIO pin.

### new GPIO\(pin\[, mode\]\)

* **`pin`** `<number>` The pin number which can support GPIO function.
* **`mode`** `<number>` The pin mode `INPUT (0)` , `OUTPUT (1)` , `INPUT_PULLUP (2)` or `INPUT_PULLDOWN (3)` . **Default:** `INPUT`

Instances of the GPIO class can be created using the new keyword or by calling gpio.GPIO\(\) as a function.

```javascript
// Javascript example: Create the GPIO instance 
var GPIO = require('gpio').GPIO;
var pin = new GPIO(0, OUTPUT);

// or, shortly
var pin = board.gpio(0, OUTPUT);
```

### gpio.read\(\)

* **Returns:** `<number>` The return value is `HIGH (1)` or `LOW (0)`

Read the value from the GPIO pin.

```javascript
// Javascript example: Read value from the pin 0.
var pin = board.gpio(0, INPUT);
var value = pin.read();
```

### gpio.write\(value\)

* **`value`** `<number>` The value could be `HIGH (1)` or `LOW (0)`.

Writes a value to the GPIO pin.

```javascript
// Javascript example: Write HIGH to the pin 0.
var pin = board.gpio(0, OUTPUT);
pin.write(HIGH);
```

### gpio.toggle\(\)

Toggles the output value of the GPIO pin.

```javascript
// Javascript example: Write LOW to the pin 0 and toggling it.
var pin = board.gpio(0, OUTPUT);
pin.write(LOW); // Set to LOW
pin.toggle(); // HIGH
pin.toggle(); // LOW
```

### gpio.low\(\)

Set the GPIO pin to `LOW`.

```javascript
var pin = board.gpio(0, OUTPUT);
pin.low();
```

### gpio.high\(\)

Set the GPIO pin to `HIGH`.

```javascript
var pin = board.gpio(0, OUTPUT);
pin.high();
```

### gpio.pin

* `<number>`

Pin number of the GPIO object.

```javascript
// Javascript example: Write LOW to the pin 0 and print the pin number.
var gpio0 = board.gpio(0, OUTPUT);
console.log(gpio0.pin) // Print pin number 0.
```

### gpio.mode

* `<number>`

Current mode of the GPIO pin. The value is `INPUT (0)` , `OUTPUT (1)` , `INPUT_PULLUP (2)` , or `INPUT_PULLDOWN (3)` .

```javascript
// Javascript example: Write LOW to the pin 0 and print the mode.
var gpio0 = board.gpio(0, OUTPUT);
console.log(gpio0.mode) // Print pin number 0.
```

