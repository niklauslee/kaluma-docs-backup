# Button

The `button` module supports button. Use `require('button')` to access this module.

## Class: Button

An instances of `Button` represents a button object. This class is a subclass of [`EventEmitter`](events.md).

### new Button\(pin\[, event\[, debounce\[, int\_pull\]\]\]\)

* **`pin`** `<number>` The pin number which can support button function.
* **`event`** `<number>` The the event of the **`pin`**. There are three events, `FALLING (0)`, `RISING (1)`, and `CHANGE (2)`. **Default:** `FALLING`.
* **`debounce`** `<number>` debounce time in ms\(milliseconds\). **Default:** `50`ms
* **`int_pull`** `<number>` Chip internal pull mode of the button. If button has a external pull up or pull down circuit, it needs to be set to `PULL_NO`. There are three pull modes, `PULL_NO (0)`, `PULL_UP (1)` or `PULL_DOWN (2)`. **Default:** `PULL_NO`

Instances of the Button class can be created using the new keyword or by calling button.Button\(\) as a function.

```javascript
// Javascript example: Create the Button instance and print the message when button is pressed.
var Button = require('button').Button;
var btn0 = new Button(board.button_pins[0]);
btn0.on('click', function () {
  console.log('button 1 clicked');
})
```

### button.read\(\)

* **Returns:** `<number>` The return value is `HIGH (1)` or `LOW (0)`

```javascript
// Javascript example: Create the Button instance and close it.
var Button = require('button').Button;
var btn0 = new Button(board.button_pins[0]);
// ...
btn0.close();
```

### button.close\(\)

This method closes the I/O watcher for the button.

```javascript
// Javascript example: Create the Button instance and close it.
var Button = require('button').Button;
var btn0 = new Button(board.button_pins[0]);
btn0.on('click', function () {
  console.log('button 1 clicked');
})
// ...
btn0.close();
```

### Event: 'click'

The `click` event is emitted when the button is pressed down.

```javascript
// Javascript example: Create the Button instance and toggle LED0 when the button is pressed.
var Button = require('button').Button;
var btn0 = new Button(board.button_pins[0]);
btn.on('click', function () {
  board.LED0.toggle();
})
```

