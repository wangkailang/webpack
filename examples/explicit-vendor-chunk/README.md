# webpack.config.js

```javascript
var path = require("path");
var webpack = require("../../");
module.exports = [
	{
		name: "vendor",
		// mode: "development || "production",
		entry: ["./vendor", "./vendor2"],
		output: {
			path: path.resolve(__dirname, "dist"),
			filename: "vendor.js",
			library: "vendor_[fullhash]"
		},
		plugins: [
			new webpack.DllPlugin({
				name: "vendor_[fullhash]",
				path: path.resolve(__dirname, "dist/manifest.json")
			})
		]
	},

	{
		name: "app",
		// mode: "development || "production",
		dependencies: ["vendor"],
		entry: {
			pageA: "./pageA",
			pageB: "./pageB",
			pageC: "./pageC"
		},
		output: {
			path: path.join(__dirname, "dist"),
			filename: "[name].js"
		},
		plugins: [
			new webpack.DllReferencePlugin({
				manifest: path.resolve(__dirname, "dist/manifest.json")
			})
		]
	}
];
```

# dist/vendor.js

```javascript
var vendor_bd8c4f4f3eadc55850c4;vendor_bd8c4f4f3eadc55850c4 =
/******/ (() => { // webpackBootstrap
/******/ 	var __webpack_modules__ = ([
/* 0 */
/***/ ((module, __unused_webpack_exports, __webpack_require__) => {

module.exports = __webpack_require__;

/***/ }),
/* 1 */
/***/ ((module) => {

module.exports = "Vendor";

/***/ }),
/* 2 */
/***/ ((module) => {

module.exports = "Vendor2";

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
/******/ 	// module exports must be returned from runtime so entry inlining is disabled
/******/ 	// startup
/******/ 	// Load entry module and return exports
/******/ 	return __webpack_require__(0);
/******/ })()
;
```

# dist/pageA.js

```javascript
/******/ (() => { // webpackBootstrap
/******/ 	var __webpack_modules__ = ([
/* 0 */
/***/ ((module, __unused_webpack_exports, __webpack_require__) => {

console.log(__webpack_require__(1));
module.exports = "pageA";

/***/ }),
/* 1 */
/***/ ((module, __unused_webpack_exports, __webpack_require__) => {

module.exports = (__webpack_require__(2))(1);

/***/ }),
/* 2 */
/***/ ((module) => {

"use strict";
module.exports = vendor_bd8c4f4f3eadc55850c4;

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
/******/ 	// startup
/******/ 	// Load entry module
/******/ 	// This entry module is referenced by other modules so it can't be inlined
/******/ 	__webpack_require__(0);
/******/ })()
;
```

# Info

## Unoptimized

```
vendor:
  asset [1m[32mvendor.js[39m[22m 1.58 KiB [1m[32m[emitted][39m[22m (name: main)
  [1mdll main[39m[22m 12 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1m./vendor.js[39m[22m 26 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1m./vendor2.js[39m[22m 27 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mvendor[39m[22m (webpack 5.10.2) compiled [1m[32msuccessfully[39m[22m

app:
  asset [1m[32mpageB.js[39m[22m 1.62 KiB [1m[32m[emitted][39m[22m (name: pageB)
  asset [1m[32mpageA.js[39m[22m 1.61 KiB [1m[32m[emitted][39m[22m (name: pageA)
  asset [1m[32mpageC.js[39m[22m 1.3 KiB [1m[32m[emitted][39m[22m (name: pageC)
  cacheable modules 144 bytes
    [1m./pageA.js[39m[22m 59 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
    [1m./pageB.js[39m[22m 60 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
    [1m./pageC.js[39m[22m 25 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  modules by path [1mdelegated ./*.js from dll-reference vendor_bd8c4f4f3eadc55850c4[39m[22m 84 bytes
    [1mdelegated ./vendor.js from dll-reference vendor_bd8c4f4f3eadc55850c4[39m[22m 42 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
    [1mdelegated ./vendor2.js from dll-reference vendor_bd8c4f4f3eadc55850c4[39m[22m 42 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mexternal "vendor_bd8c4f4f3eadc55850c4"[39m[22m 42 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mapp[39m[22m (webpack 5.10.2) compiled [1m[32msuccessfully[39m[22m
```

## Production mode

```
vendor:
  asset [1m[32mvendor.js[39m[22m 283 bytes [1m[32m[emitted][39m[22m [1m[32m[minimized][39m[22m (name: main)
  [1mdll main[39m[22m 12 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1m./vendor.js[39m[22m 26 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1m./vendor2.js[39m[22m 27 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mvendor[39m[22m (webpack 5.10.2) compiled [1m[32msuccessfully[39m[22m

app:
  asset [1m[32mpageA.js[39m[22m 283 bytes [1m[32m[emitted][39m[22m [1m[32m[minimized][39m[22m (name: pageA)
  asset [1m[32mpageB.js[39m[22m 283 bytes [1m[32m[emitted][39m[22m [1m[32m[minimized][39m[22m (name: pageB)
  asset [1m[32mpageC.js[39m[22m 160 bytes [1m[32m[emitted][39m[22m [1m[32m[minimized][39m[22m (name: pageC)
  cacheable modules 144 bytes
    [1m./pageA.js[39m[22m 59 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
    [1m./pageB.js[39m[22m 60 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
    [1m./pageC.js[39m[22m 25 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  modules by path [1mdelegated ./*.js from dll-reference vendor_5bfab807ffd8b99ce903[39m[22m 84 bytes
    [1mdelegated ./vendor.js from dll-reference vendor_5bfab807ffd8b99ce903[39m[22m 42 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
    [1mdelegated ./vendor2.js from dll-reference vendor_5bfab807ffd8b99ce903[39m[22m 42 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mexternal "vendor_5bfab807ffd8b99ce903"[39m[22m 42 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
  [1mapp[39m[22m (webpack 5.10.2) compiled [1m[32msuccessfully[39m[22m
```
