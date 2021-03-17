# Digital I/O

## pinMode\(pin\[, mode\]\)

* **`pin`** `<number>` The pin number which can support GPIO function.
* **`mode`** `<number>` The pin mode `INPUT (0)` or `OUTPUT (1)`or `INPUT_PULLUP (2)`

  . **Default:** `INPUT`

Set the mode of the GPIO **`pin`** to `INPUT` or `OUTPUT`or `INPUT_PULLUP`. A `RangeError` will be thrown if **`pin`** does not support GPIO function. Use `INPUT_PULLUP`when you want to enable internal pull-up for this **`pin`**.

```javascript
// Javascript example: Set pin 1 to OUTPUT HIGH.
pinMode(1, OUTPUT); // Set the pin 1 to OUTPUT.
digitalWrite(1, HIGH); // Set the pin 1 to HIGH.
```

## digitalRead\(pin\)

* **`pin`** `<number>` The pin number which can support GPIO function.
* **Returns:** `<number>` The return value is `HIGH (1)` or `LOW (0)`

Read the digital input from the GPIO INPUT **`pin`**. A `RangeError` will be thrown if **`pin`** does not support GPIO function.

```javascript
// Javascript example: Read value from the pin 1.
pinMode(1, INPUT); // Set the pin 1 to GPIO INPUT
var value = digitalRead(1); // Read the digital input value from the pin 1.
```

## digitalWrite\(pin\[, value\]\)

* **`pin`** `<number>` The pin number which can support GPIO function.
* **`value`** `<number>` The value could be `HIGH (1)` or `LOW (0)`. **Default:** `LOW`

Set the GPIO OUTPUT **`pin`** to `HIGH` or `LOW`. A `RangeError` will be thrown if **`pin`** does not support GPIO function.

```javascript
// Javascript example: Set the pin 1 to HIGH.
pinMode(1, OUTPUT); // Set the pin 1 to GPIO OUTPUT
digitalWrite(1, HIGH); // Set the pin 1 to HIGH
```

## digitalToggle\(pin\)

* **`pin`** `<number>` The pin number which can support GPIO function.

Set the GPIO OUTPUT **`pin`** to the reverse state of the current state. Set to `HIGH` if the current state is `LOW`. Set to `LOW` if the current state is `HIGH`. A `RangeError` will be thrown if **`pin`** does not support GPIO function.

```javascript
// Javascript example: Set the pin 1 to HIGH and toggle (Set to LOW)
pinMode(1, OUTPUT); // Set the pin 1 to GPIO OUTPUT
digitalWrite(1, HIGH); // Set the pin 1 to HIGH
digitalToggle(1) // Toggle the pin 1, change the pin state to LOW from HIGH.
```

## setWatch\(callback, pin\[, event\[, debounce\]\]\)

* **`callback`** `<function>` The function is called when the `pin` event is triggered. 
* **`pin`** `<number>` The pin number which can support GPIO function.
* **`event`** `<number>` set the event of the `pin`. There are three events, `FALLING (0)`, `RISING (1)`, and `CHANGE (2)`. **Default:** `FALLING`.
* **`debounce`** `<number>` debounce time in ms\(milliseconds\). **Default:** `0`ms
* **Returns:** `<number>` the ID of the watcher.

Run the **`callback`** function when the **`event`** is triggered on the **`pin`**. There are three events. The `FALLING` event is triggered when the **`pin`** state is changed from `HIGH` to `LOW`. The `RISING (1)` event is triggered when the **`pin`** state is changed from `LOW` to `HIGH`. The `CHANGE` event is triggered when the **`pin`** state is changed to any states, which means the `CHANGE` event is the same as the `FALLING` + `RISING` events. The **`debounce`** time can be set when you can see the bouncing on the GPIO **`pin`**. A `RangeError` will be thrown if **`pin`** does not support GPIO function.

Before calling this function, you have to set the pin mode as `INPUT` or `INPUT_PULLUP`.

```javascript
// Javascript example: Print out 'click' string to the terminal when user press the button.
var pin = board.button_pins[0]; // Set the pin to the the on-board button
pinMode(pin, INPUT); // Set the pin mode to INPUT.
var id = setWatch(function () {
  console.log("click"); // Print out the 'click' to the terminal.
}, pin, FALLING, 10); // Set falling event with 10ms debouncing time.
```

## clearWatch\(id\)

* **`id`** `<number>` The ID of the watcher which is the return value of the `setWatch()` function.

Stop watching the event which is set by `setWatch()` function.

```javascript
// Javascript example: Print out 'click' string to the terminal when user press the button.
var pin = board.button_pins[0]; // Set the pin to the the on-board button
pinMode(pin, INPUT); // Set the pin mode to INPUT.
var id = setWatch(function () {
  console.log("click"); // Print out the 'click' to the terminal.
}, pin, FALLING, 10); // Set falling event with 10ms debouncing time.
clearWatch(id); // Stop watching the on-board pin event.
```

## pulseRead\(pin, count\[, timeout\[, startState\]\]\)

* **`pin`** `<number>` The pin number which can support GPIO function.
* **`count`** `<number>` The number of pulse to read.
* **`timeout`** `<number>` timeout in us\(microseconds\). **Default:** `5`s
* **`startState`** `<number>` Start to read the pulse from this state. **Default:** `undefined`
* **Returns:** `<Array>` Array of the pulse timing. It returns `null` if the pin state is not changed until **`timeout`**

Read the **`pin`**state change timing from **`startState`**. It returns the microseconds state changing timing if the state is changed **`count`** times or for **`timeout`** microseconds.

If **`startState`** is `HIGH (1)` the system wait until the pin state to `HIGH` and start to measure pulse timing. The If **`startState`** is`undefined`, the system start to measure pulse timing immediately and user can't know which pulse timing is `HIGH` or `LOW`.

You should be consider the CPU process time in the very first output array data. This means that the very first timing data is less than your expected timing due to CPU process time. Please see the below pictures for a better understanding.



```javascript
// Javascript example: Print out pulse timing on the pin 0
pinMode(0, INPUT);
var pulse = pulseRead(0, 10); // read 10 pulse timing
if (pulse !== null) {
  console.log (pulse); // Print out the pulse timing array.
}
// read 10 pulse timing with 50ms timeout.
// The first data is the microsecond timing of the LOW state.
pinMode(0, INPUT);
pulse = pulseRead(0, 10, 50000, LOW); 
if (pulse !== null) {
  console.log (pulse); // [10, 20, 10, 20, 10, 20, 10, 20, 10, 20]
}
```

## pulseWrite\(pin, startState, interval\)

* **`pin`** `<number>` The pin number which can support GPIO function.
* **`startState`** `<number>` Start to read the pulse from this state.
* **`interval`** `<Array>` microseconds pulse timing. 
* **Returns:** `<number>` Length of the written pulse, it's the same as the length of the **`interval`** array.

Make the digital pulse on the **`pin`**with microseconds timing. The state change timing from **`startState`**. It returns the number of the written pulse.

```javascript
// Javascript example: Make pulse on the pin 0
pinMode(0, OUTPUT);
pulseWrite(0, HIGH, [10,20,30,50,100,1000,2000,3000,50000,70000,100000]);
```

