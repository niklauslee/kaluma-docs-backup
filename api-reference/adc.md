# ADC

The `adc` module provides the ADC class which supports analog-digital conversion. Use `require('adc')` to access this module.

## Class: ADC

An instances of `ADC` represents a ADC object.

### new ADC\(pin\)

* **`pin`** `<number>` The pin number which can support ADC function.
* **Returns:** `<object>` The return value is `ADC` object.

Instances of the `ADC` class can be created using the new keyword or by calling adc.ADC\(\) as a function.

```javascript
// Javascript example: Create the ADC instance with pin 3 and read the value.
var ADC = require('adc').ADC;
var a3 = new ADC(3); // Create the ADC instance with pin 3
var val = a3.read(); // Read the ADC value at the pin 3.
```

```javascript
// Javascript example: Create the ADC instance with pin 3 and read the value.
var a3 = board.adc(3); // Create the ADC instance with pin 3
var val = a3.read(); // Read the ADC value at the pin 3.
```

### adc.read\(\)

* **Returns:** `<number>` The return value is ADC object.

This method returns the analog value read from the pin. A `RangeError` will be thrown if **`adc.pin`** does not support ADC function.

```javascript
// Javascript example: Create the ADC instance with pin 3 and read the value.
var a3 = board.adc(3); // Create the ADC instance with pin 3
var value = a3.read(); // Read the ADC value at the pin 3.
```

### adc.pin

* `<number>` The pin number which can support ADC function.

The pin number of the ADC object.

```javascript
// Javascript example: Create the ADC instance with pin 3 and read the value.
var ADC = require('adc').ADC;
var a3 = new ADC(3); // Create the ADC instance with pin 3
a3.pin; // the vaue is 3
```

