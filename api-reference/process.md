# Process

* The `process` object provide the information about a Kameleon process.

## Object: process

### process.arch

* `<string>`ex\) 'arm', 'x64', ...

The system architecture which the Kameleon FW is compiled. 

### process.platform

* `<string>`ex\) 'linux', 'darwin', 'unknown', ...

The OS system which the Kameleon FW is running.

### process.version

* `<string>`version number, emver format. ex\) '0.1.0', ...

### process.builtin\_modules

* `<string[]>`array of built-in module names. 

There's no need to use `require` before using the built-in module.

### process.getBuiltinModule\(builtin\_module\_name\)

* **`builtin_module_name`** `<string>`
* **Returns:** `<function>` 

load the builtin module and return the module as a function

### process.binding\(native\_module\_name\)

* **`native_module_name`** `<string>`
* **Returns:** `<function>`

load a native module

Has properties  : binding has native module names as properties

