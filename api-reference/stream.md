# Stream

This `steam` module provides abstract interfaces for working with streaming data. Use `require('stream')` to access this module.

## Class: Stream

* Extends: [`EventEmitter`](events.md#class-eventemitter) 

This is an abstract class of streams.

### stream.destroy\(\)

* Returns: `{this}`

Closes the stream.

### Event: 'close'

Emitted when the stream is closed.

## Class: Readable

* Extends: [`stream.Stream`](stream.md#class-stream) 

Readable streams are an abstraction for a _source_ from which data is consumed. This is a condensed version of Readable stream in [Node.js](https://nodejs.org).

### readable.readableEnded

* `{boolean}`

Becomes `true` when [`'end'`](stream.md#event-end) event is emitted.

### readable.push\(chunk\)

* **`chunk`** `{Uint8Array}` 

_This function should not be called in application code. It is only for stream implementors._ This should be called when a chunk of data is arrived from the stream.

### Event: 'data'

* **`chunk`** `{Uint8Array}` 

Emitted whenever a chunk of data is available to consume.

### Event: 'end'

Emitted when all data completely consumed and no more data to read.

### Event: 'error'

* **`err`** `{Error}`

Emitted when error occurred.

## Class: Writable

* Extends: [`stream.Stream`](stream.md#class-stream) 

Writable streams are an abstraction for a _destination_ to which data is written. This is a condensed version of Writable stream in [Node.js](https://nodejs.org).

### writable.writableEnded

* `{boolean}`

Becomes `true` when [`writable.end()`](stream.md#writable-end-chunk-callback) is called.

### writable.writableFinished

* `{boolean}`

Becomes `true` when [`'finish'`](stream.md#event-finish) event is emitted.

### writable.write\(chunk\[, callback\]\)

* **`chunk`** `{Uint8Array|string}` A chunk of data to write.
* **`callback`** `{Function}` Called when the chunk of data is handled.
* Returns: `{boolean}` 

Writes a chunk of data on the stream. It returns `true` if the stream is ready to handle the next chunk of data. It returns `false`, then the stream will emit [`'drain'`](stream.md#event-drain) event when the all data written are handled and the internal buffer is empty. If you write data before [`'drain'`](stream.md#event-drain) event emitted, the chunk of data will be appended to the internal buffer.

### writable.end\(\[chunk\]\[, callback\]\)

* **`chunk`** `{Uint8Array|string}` A chunk of data to write before finish.
* **`callback`** `{Function}` Called when the stream is finished.
* Returns: `{this}` 

Finishes to write data on the stream. The event [`'finish'`](stream.md#event-finish) will be emitted after successfully finished.

### writable.\_write\(chunk\[, callback\]\)

* **`chunk`** `{Uint8Array|string}` 
* **`callback`** `{Function}` 

_This function should not be called in application code. It is only for stream implementors._ This function must be implemented in the inherited stream classes.

### writable.\_final\(\[callback\]\)

* **`callback`** `{Function}` 

_This function should not be called in application code. It is only for stream implementors._ This function must be implemented in the inherited stream classes. 

### Event: 'drain'

Emitted when the stream is ready to write and the internal buffer is empty.

### Event: 'finish'

Emitted when the stream is finished.

### Event: 'error'

* **`err`** `{Error}`

Emitted when error occurred.

## Class: stream.Duplex

Extends: [`stream.Readable`](stream.md#class-readable), [`stream.Writable`](stream.md#class-writable)

Duplex streams are streams that implement both the [Readable](stream.md#class-readable) and [Writable](stream.md#class-writable) interfaces.



