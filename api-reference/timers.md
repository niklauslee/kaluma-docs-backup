# Timers

## delay\(msec\)

* **`msec`** `<number>` The delay value in milliseconds.

Wait for **`msec`** milliseconds.

> This function would block all the process for **`msec`**  milliseconds, so please use it carefully. it may block the Kameleon console and REPL. [`setTimeout`](timers.md#settimeout-callback-timeout), [`setInterval`](timers.md#setinterval-callback-interval) is strongly recommended instead of this function.

```javascript
// Javascript example: Wait for 3 sec.
delay(3000); // delay 3 seconds.
```

## millis\(\)

* **Returns:** `<number>` The current timestamp in milliseconds.

Returns the number of milliseconds elapsed since January 1, 1970 00:00:00 UTC.

```javascript
// Javascript example: Show the processing time of the function.
var startTime = millis(); // store start time.
for (var i = 1; i <= 10; i++)
  console.log ("Processing...", i * 10, "%");
var endTime = millis(); //store end time.
console.log ("Processing time is ", endTime - startTime, "ms.");
```

## setTimeout\(callback, timeout\)

* **`callback`** `<function>` The function which is called after **`timeout`** milliseconds
* **`timeout`** `<number>` The timeout value in milliseconds.
* **Returns**: `<number>` Timer id.

Set the timeout event which call the **`callback`** function after **`delay`** milliseconds.

```javascript
// Javascript example: Show the message after 1 sec.
var timerId = setTimeout(function () {
  print('done.');
}, 1000); // 1sec timeout
```

## setInterval\(callback, interval\)

* **`callback`** `<function>` The function which is called at every **`interval`** milliseconds.
* **`interval`** `<number>` The time interval value in milliseconds.
* **Returns**: `<number>` Timer id.

Set the interval event which call the **`callback`** function every**`interval`** milliseconds.

```javascript
// Javascript example: Print "tick" for every seconds
var timerId = setInterval(function () {
  print('tick');
}, 1000); // 1sec interval
// ...
clearInterval(timerId); // To stop printing "tick"
```

## clearTimeout\(id\)

* **`id`** `<number>` Timer id.

Clear timeout event which is set using `setTimeout()`.

```javascript
// Javascript example: Show the message after 1 sec.
var timerId = setTimeout(function () {
  print('done.');
}, 1000); // 1sec timeout
// ...
clearTimeout(timerId); // clear it after the timeout event.
```

## clearInterval\(id\)

* **`id`** `<number>` Timer id.

Clear interval event which is set using `setInterval()`.

```javascript
// Javascript example: Print "tick" for every seconds and clear it.
var timerId = setInterval(function () {
  print('tick');
}, 1000); // 1sec interval
// ...
clearInterval(timerId); // clear it to stop printing "tick"
```

