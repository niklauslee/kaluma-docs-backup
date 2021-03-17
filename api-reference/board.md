# Board

The `board` object provide the board specific functions and properties which you are currently using.

## Object: board

### board.name

* `<string>`

The ID of the target board. ex\) `kameleon-core`, ...

```javascript
// Javascript example: Print out the ID of the board.
console.log(board.name)  // The output is kameleon-core with Kameleon Core board.
```

### board.NUM\_GPIO

* `<number>` 

The total number of GPIO.

```javascript
// Javascript example: Print out the numeber of GPIO pins on your board.
console.log(board.NUM_GPIO) // The output is 22 with Kameleon Core board.
```

### board.NUM\_LED

* `<number>` 

The total number of on-board LEDs.

```javascript
// Javascript example: Print out the number of on-board LEDs on your board.
console.log(board.NUM_LED) // The output is 1 with Kameleon Core board.
```

### board.NUM\_BUTTON

* `<number>`

The total number of on-board buttons.

```javascript
// Javascript example: Print out the number of on-board button on your board.
console.log(board.NUM_BUTTON) // The output is 1 with Kameleon Core board.
```

### board.NUM\_PWM

* `<number>` 

The total number of PWM channels.

```javascript
// Javascript example: Print out the number of PWM channels on your board.
console.log(board.NUM_PWM) // The output is 5 with Kameleon Core board.
```

### board.NUM\_ADC

* `<number>` 

The total number of ADCs \(Analog-Digital Converter\).

```javascript
// Javascript example: Print out the number of ADC on your board.
console.log(board.NUM_ADC) // The output is 6 with Kameleon Core board.
```

### board.NUM\_I2C

* `<number>` 

The total number of I2C buses.

```javascript
// Javascript example: Print out the number of I2C on your board.
console.log(board.NUM_I2C) // The output is 2 with Kameleon Core board.
```

### board.NUM\_SPI

* `<number>`  

The total number of SPI buses.

```javascript
// Javascript example: Print out the number of SPI on your board.
console.log(board.NUM_SPI) // The output is 2 with Kameleon Core board.
```

### board.NUM\_UART

* `<number>` 

The total number of UART ports.

```javascript
// Javascript example: Print out the number of UART on your board.
console.log(board.NUM_UART) // The output is 2 with Kameleon Core board.
```

### board.led\_pins

* `<number[]>` 

The arrary of pin numbers which can support on-board LED.

```javascript
// Javascript example: Print out the pin numbers of on-board LED on your board.
console.log(board.led_pins) // The output is [20] with Kameleon Core board.
```

### board.button\_pins

* `<number[]>` 

The arrary of pin numbers which can support on-board button.

```javascript
// Javascript example: Print out the pin numbers of on-board button on your board.
console.log(board.button_pins) // The output is [21] with Kameleon Core board.
```

### board.pwm\_pins

* `<number[]>` 

The arrary of pin numbers which can support PWM function.

```javascript
// Javascript example: Print out the pin numbers of PWM on your board.
console.log(board.pwm_pins) // The output is [1,2,14,15,16] with Kameleon Core board.
```

### board.adc\_pins

* `<number[]>` 

The arrary of pin numbers which can support ADC function.

```javascript
// Javascript example: Print out the pin numbers of ADC on your board.
console.log(board.adc_pins) // The output is [3,4,5,10,11,12] with Kameleon Core board.
```

### board.gpio\(pin\[, mode\]\)

* **`pin`** `<number>` The pin number which can support GPIO function.
* **`mode`** `<number>` The pin mode `INPUT (0)` , `OUTPUT (1)` or `INPUT_PULLUP (2)` **Default:** `INPUT`
* **Returns:** `<object>` An initialized `GPIO` instance corresponds to the pin number.

Return a [GPIO object](gpio.md) corresponds to the pin number.

```javascript
// Javascript example: Set GPIO pin 5 to HIGH
var gpio5 = board.gpio(5, OUTPUT); // Get GPIO object with pin 5
gpio5.write(HIGH); // Set GPIO5 to HIGH
```

### board.led\(pin\)

* **`pin`** `<number>` The pin number which can support GPIO function.
* **Returns:** `<object>` An initialized `LED` instance corresponds to the pin number.

Return a [LED object](led.md) corresponds to the pin number.

```javascript
// Javascript example: Turn on the LED on the pin 0
var led = board.led(0); // Get LED object with pin 0
led.on(); // Turn on the LED on the pin 0.
```

### board.button\(pin\[, event\[, debounce\[, int\_pull\]\]\]\)

* **`pin`** `<number>` The pin number which can support button function.
* **`event`** `<number>` The the event of the **`pin`**. There are three events, `FALLING (0)`, `RISING (1)`, and `CHANGE (2)`. **Default:** `FALLING`.
* **`debounce`** `<number>` debounce time in ms\(milliseconds\). **Default:** `50`ms
* **`int_pull`** `<number>` Chip internal pull mode of the button. If button has a external pull up or pull down circuit, it needs to be set to `PULL_NO`. There are three pull modes, `PULL_NO (0)`, `PULL_UP (1)` or `PULL_DOWN (2)`. **Default:** `PULL_NO`
* **Returns:** `<object>` An initialized `BUTTON` instance corresponds to the pin number.

Return a [button object](button.md) corresponds to the pin number.

```javascript
// Javascript example: Print out the message when the on-board button is pressed.
var btn0 = board.button(board.button_pins[0], PULL_UP, 100); // Get the button object from on-board button
btn0.on('click', function () { // Print out the message when the button is pressed.
  console.log('button 1 clicked');
})
```

### board.pwm\(pin\[, frequency\[, duty\]\]\)

* **`pin`** `<number>` The pin number which can support PWM function.
* **`freq`** `<number>` Frequency in Hz. **Default:** `490` Hz.
* **`duty`** `<number>` Duty cycle between `0.0` and `1.0`. **Default:** `1.0` \(100% duty\)
* **Returns:** `<object>` An initialized `PWM` instance corresponds to the pin number.

Return a [PWM object](pwm.md) corresponds to the pin number.

```javascript
// Javascript example: Print out the message when the on-board button is pressed.
var pwm1 = board.pwm(1, 100, 0.4); // Get the pwm object on pin 1
pwm1.start(); // Generate PWM signal on the pin 1.
})
```

### board.adc\(pin\)

* **`pin`** `<number>` The pin number which can support ADC function.
* **Returns:** `<object>` An initialized `ADC` instance corresponds to the pin number.

Return an [ADC object](adc.md) corresponds to the pin number.

```javascript
// Javascript example: Read ADC value on the pin 3.
var adc3 = board.adc(3); // Get the adc object on pin 3
adc.read(); // Read ADC value on the pin 3.
})
```

### board.i2c\(bus\[, mode \[, mode\_option\]\]\)

* **`bus`** `<number>` Bus number. This value shold be less than board.NUM\_I2C
* **`mode`** `<number>` I2C mode, `0` for master mode or `1` for slave mode. **Default:** `0`
* **`mode_option`** `<number>` Clock speed \(bit/s\) for Master mode. **Default:** `100000`
* **Returns:** `<object>` An initialized `I2C` instance corresponds to the bus number.

> * Slave Mode is NOT supported in this version but we'll suport it soon.

Return [I2C object](i2c.md) initialized with the bus number

```javascript
// Javascript example: Create the I2C instance with master mode and close it.
var i2c0 = board.i2c(0); 
// Write or Read from I2C
i2c0.close(); // Close i2c device
```

### board.spi\(bus\[, options\]\)

* **`bus`** `<number>` SPI bus number. This value shold be less than board.NUM\_SPI
* **`options`** `<object>` The object of SPI options. mode,  baudrate, bitorder and bits are defined in this object.
  * **`mode`** `<number>` `SPI.MODE_0 (0)` \(CPOL=0/CPHA=0\), `SPI.MODE_1 (1)` \(CPOL=0/CPHA=1\), `SPI.MODE_2 (2)` \(CPOL=1/CPHA=0\), or `SPI.MODE_3 (3)` \(CPOL=1/CPHA=1\). **Default:** `SPI.MODE_0`.
  * **`baudrate`** `<number>` Baud rate. **Default:** `3000000`, 3 Mbit/s
  * **`bitorder`** `<number>` `SPI.MSB (0)` or `SPI.LSB (1)`  **Default:** `SPI.MSB (0)`
* **Returns:** `<object>` An initialized `SPI` instance corresponds to the bus number. Once initialized, the same object will be returned.

Return [SPI object](spi.md) initialized with the bus number

### board.uart\(port\[, options\]\)

* **`port`** `<number>` The pin number which can support UART function.
* **`options`** `<object>` The same options of the UART object to the `setup()` method.
* **Returns:** `<object>` An initialized `UART` instance corresponds to the port number. Once initialized, the same object will be returned.

Return [UART object](uart.md) initialized with the port number

### board.LED0

* `<object>` `LED` object for the on-board LED. \(Readonly\)

Indicates the on-board LED \(`LED0`\). Some board may not have LED0.

```javascript
// Javascript example: Turn on the on-board LED0
LED0.on(); // Turn on the on-board LED0
```

### board.BTN0

* `<Button>` `Button` object for the on-board Button. \(Readonly\)

Indicates the on-board button \(`BTN0`\). Some board may not have BTN0.

```javascript
// Javascript example: Print out the message when the on-board button is pressed.
board.BTN0.on('click', function () { // Print out the message when the button is pressed.
  console.log('button 1 clicked');
})
```

