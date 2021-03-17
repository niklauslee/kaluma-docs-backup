# Project Configuration

You can configure project with `package.json`

```javascript
{
  "name": "my-project",
  "dependencies": {
    "@niklauslee/ssd1306": "1.0.0"
  },
  "main": "index.js",
  "bundle": {
    "mode": "development"
  }
}
```

* **`name`** `<string>` Project name.
* **`dependencies`** `<Object<string,string>>` Module dependencies with module name and version like `"@owner/package": "1.0.0"`.
* **`main`** `<string>` The entry point of the module. The file specified by this property is loaded when this module is imported by `require()` form other products. Default: `index.js`.
* **`bundle`** `<object>` Configuration for code bundling.
  * **`mode`** `<string>` Bundling mode is `development` or `production`. In `development` mode, the code is bundled _as-is \(not minified\)_ so it is readable and and easier to debug. Whereas in `production` mode, the bundled code is minified so it is smaller and faster but not useful for debugging. Default: `development`.



