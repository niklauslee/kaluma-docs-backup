# Analog I/O

## analogRead\(pin\)

* **`pin`** `<number>` The pin number which can support ADC function.
* **Returns:** `<number>`, the value is in between `0.0` ~ `1.0`

Read and return analog signal value from the ADC **`pin`**. A `RangeError` will be thrown if the **`pin`** does not support ADC function.

```javascript
// Javascript example: Read analog signal value on the adc_pins[0]
var pin = board.adc_pins[0]; // Get an analog pin number
var value = analogRead(pin); // Read analog signal value on the pin.
```

## analogWrite\(pin\[, duty\[, frequency\]\]\)

* **`pin`** `<number>` The pin number which can support PWM function.
* **`duty`** `<number>` The PWM duty cycle between `0.0` and `1.0`. **Default:** `0.5`
* **`frequency`** `<number>` The PWM frequency in Hz. **Default:** `490`Hz

Generate PWM signal with specific **`frequency`** and **`duty`** to the PWM **`pin`**. A `RangeError` will be thrown if **`pin`** does not support PWM function.

```javascript
// Javascript example: Generate 490 Hz 50% duth PWM signal on the pwm_pins[0]
var pin = board.pwm_pins[0]; // Get an analog pin number
analogWrite(pin, 0.5); // Generate 490 Hz 50% duty.
```

## tone\(pin\[, frequency\[, duration\[, duty\]\]\]\)

* **`pin`** `<number>` The pin number which can support PWM function.
* **`frequency`** `<number>` The PWM frequency in Hz. **Default:** `261.626`Hz \(C Key\)
* **`duration`** `<number>` The duration in milliseconds if a duration is not 0, duration 0 is forever. **Default:** `0`
* **`duty`** `<number>` The PWM duty cycle between `0.0` and `1.0`. **Default:** `0.5`

Generate sound tone\(PWM\) on the PWM **`pin`** for **`duration`**. A **`frequency`** and **`duty`** can be set. A `RangeError` will be thrown if **`pin`** does not support PWM function.

```javascript
// Javascript example: Generate 300 Hz tone on the pin 1 for 1sec.
tone(1, 300, 1000); // Generate 300Hz tone on the pin 1 for 1sec.
```

## noTone\(pin\)

* **`pin`** `<number>` The pin number which can support PWM function.

Stop the tone one the PWM **`pin`**. A `RangeError` will be thrown if **`pin`** does not support PWM function.

```javascript
// Javascript example: Generate 200 Hz tone to the pin 1 and stop the tone after 1sec.
tone(1, 200); // Generate 200Hz tone on the pin 1.
delay(1000); // Wait for 1000ms (1sec)
noTone(1); // Stop the tone on the pin 1
```

