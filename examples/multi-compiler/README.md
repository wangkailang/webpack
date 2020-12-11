# example.js

```javascript
if(ENV === "mobile") {
	require("./mobile-stuff");
}
console.log("Running " + ENV + " build");
```

# webpack.config.js

```javascript
var path = require("path");
var webpack = require("../../");
module.exports = [
	{
		name: "mobile",
		// mode: "development || "production",
		entry: "./example",
		output: {
			path: path.join(__dirname, "dist"),
			filename: "mobile.js"
		},
		plugins: [
			new webpack.DefinePlugin({
				ENV: JSON.stringify("mobile")
			})
		]
	},

	{
		name: "desktop",
		// mode: "development || "production",
		entry: "./example",
		output: {
			path: path.join(__dirname, "dist"),
			filename: "desktop.js"
		},
		plugins: [
			new webpack.DefinePlugin({
				ENV: JSON.stringify("desktop")
			})
		]
	}
];
```

# dist/desktop.js

```javascript
/******/ (() => { // webpackBootstrap
if(false) {}
console.log("Running " + "desktop" + " build");
/******/ })()
;
```

# dist/mobile.js

```javascript
/******/ (() => { // webpackBootstrap
/******/ 	var __webpack_modules__ = ([
/* 0 */,
/* 1 */
/***/ (() => {

// mobile only stuff

/***/ })
/******/ 	]);
```

<details><summary><code>/* webpack runtime code */</code></summary>

``` js
/************************************************************************/
/******/ 	// The module cache
/******/ 	var __webpack_module_cache__ = {};
/******/ 	
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/ 		// Check if module is in cache
/******/ 		if(__webpack_module_cache__[moduleId]) {
/******/ 			return __webpack_module_cache__[moduleId].exports;
/******/ 		}
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = __webpack_module_cache__[moduleId] = {
/******/ 			// no module.id needed
/******/ 			// no module.loaded needed
/******/ 			exports: {}
/******/ 		};
/******/ 	
/******/ 		// Execute the module function
/******/ 		__webpack_modules__[moduleId](module, module.exports, __webpack_require__);
/******/ 	
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/ 	
/************************************************************************/
```

</details>

``` js
(() => {
if(true) {
	__webpack_require__(1);
}
console.log("Running " + "mobile" + " build");
})();

/******/ })()
;
```

# Info

## Unoptimized

```
mobile:
  asset [1m[32mmobile.js[39m[22m 1.22 KiB [1m[32m[emitted][39m[22m (name: main)
  [1m./example.js[39m[22m 94 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1m./mobile-stuff.js[39m[22m 20 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mmobile[39m[22m (webpack 5.10.2) compiled [1m[32msuccessfully[39m[22m

desktop:
  asset [1m[32mdesktop.js[39m[22m 114 bytes [1m[32m[emitted][39m[22m (name: main)
  [1m./example.js[39m[22m 94 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mdesktop[39m[22m (webpack 5.10.2) compiled [1m[32msuccessfully[39m[22m
```

## Production mode

```
mobile:
  asset [1m[32mmobile.js[39m[22m 181 bytes [1m[32m[emitted][39m[22m [1m[32m[minimized][39m[22m (name: main)
  [1m./example.js[39m[22m 94 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1m./mobile-stuff.js[39m[22m 20 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mmobile[39m[22m (webpack 5.10.2) compiled [1m[32msuccessfully[39m[22m

desktop:
  asset [1m[32mdesktop.js[39m[22m 37 bytes [1m[32m[emitted][39m[22m [1m[32m[minimized][39m[22m (name: main)
  [1m./example.js[39m[22m 94 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mdesktop[39m[22m (webpack 5.10.2) compiled [1m[32msuccessfully[39m[22m
```
