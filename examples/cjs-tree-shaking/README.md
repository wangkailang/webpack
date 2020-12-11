# example.js

```javascript
const inc = require("./increment").increment;
var a = 1;
inc(a); // 2
```

# increment.js

```javascript
const add = require("./math").add;
exports.increment = function increment(val) {
	return add(val, 1);
};
exports.incrementBy2 = function incrementBy2(val) {
	return add(val, 2);
};
exports.decrement = function decrement(val) {
	return add(val, 1);
};
```

# math.js

```javascript
exports.add = function add() {
	var sum = 0,
		i = 0,
		args = arguments,
		l = args.length;
	while (i < l) {
		sum += args[i++];
	}
	return sum;
};

exports.multiply = function multiply() {
	var product = 0,
		i = 0,
		args = arguments,
		l = args.length;
	while (i < l) {
		sum *= args[i++];
	}
	return sum;
};
```

# dist/output.js

```javascript
/******/ (() => { // webpackBootstrap
/******/ 	var __webpack_modules__ = ([
/* 0 */,
/* 1 */
/*!**********************!*\
  !*** ./increment.js ***!
  \**********************/
/***/ ((__unused_webpack_module, exports, __webpack_require__) => {

var __webpack_unused_export__;
const add = __webpack_require__(/*! ./math */ 2)/* .add */ .I;
exports.nP = function increment(val) {
	return add(val, 1);
};
__webpack_unused_export__ = function incrementBy2(val) {
	return add(val, 2);
};
__webpack_unused_export__ = function decrement(val) {
	return add(val, 1);
};


/***/ }),
/* 2 */
/*!*****************!*\
  !*** ./math.js ***!
  \*****************/
/***/ ((__unused_webpack_module, exports) => {

var __webpack_unused_export__;
exports.I = function add() {
	var sum = 0,
		i = 0,
		args = arguments,
		l = args.length;
	while (i < l) {
		sum += args[i++];
	}
	return sum;
};

__webpack_unused_export__ = function multiply() {
	var product = 0,
		i = 0,
		args = arguments,
		l = args.length;
	while (i < l) {
		sum *= args[i++];
	}
	return sum;
};


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
/*!********************!*\
  !*** ./example.js ***!
  \********************/
const inc = __webpack_require__(/*! ./increment */ 1)/* .increment */ .nP;
var a = 1;
inc(a); // 2

})();

/******/ })()
;
```

# dist/output.js (production)

```javascript
/*! For license information please see output.js.LICENSE.txt */
(()=>{var r=[,(r,n,t)=>{const e=t(2).I;n.nP=function(r){return e(r,1)}},(r,n)=>{n.I=function(){for(var r=0,n=0,t=arguments,e=t.length;n<e;)r+=t[n++];return r}}],n={};(0,function t(e){if(n[e])return n[e].exports;var o=n[e]={exports:{}};return r[e](o,o.exports,t),o.exports}(1).nP)(1)})();
```

# dist/without.js (same without tree shaking)

```javascript
/*! For license information please see without.js.LICENSE.txt */
(()=>{var n=[,(n,r,t)=>{const e=t(2).add;r.increment=function(n){return e(n,1)},r.incrementBy2=function(n){return e(n,2)},r.decrement=function(n){return e(n,1)}},(n,r)=>{r.add=function(){for(var n=0,r=0,t=arguments,e=t.length;r<e;)n+=t[r++];return n},r.multiply=function(){for(var n=0,r=arguments,t=r.length;n<t;)sum*=r[n++];return sum}}],r={};(0,function t(e){if(r[e])return r[e].exports;var u=r[e]={exports:{}};return n[e](u,u.exports,t),u.exports}(1).increment)(1)})();
```

# Info

## Unoptimized

```
asset [1m[32moutput.js[39m[22m 2.21 KiB [1m[32m[emitted][39m[22m (name: main)
[1m./example.js[39m[22m 70 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
[1m./increment.js[39m[22m 251 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
[1m./math.js[39m[22m 313 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.2 compiled [1m[32msuccessfully[39m[22m

asset [1m[32mwithout.js[39m[22m 2.12 KiB [1m[32m[emitted][39m[22m (name: main)
[1m./example.js[39m[22m 70 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
[1m./increment.js[39m[22m 251 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
[1m./math.js[39m[22m 313 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.2 compiled [1m[32msuccessfully[39m[22m
```

## Production mode

```
asset [1m[32moutput.js[39m[22m 351 bytes [1m[32m[emitted][39m[22m [1m[32m[minimized][39m[22m (name: main) 1 related asset
[1m./example.js[39m[22m 70 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
[1m./increment.js[39m[22m 251 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
[1m./math.js[39m[22m 313 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.2 compiled [1m[32msuccessfully[39m[22m

asset [1m[32mwithout.js[39m[22m 537 bytes [1m[32m[emitted][39m[22m [1m[32m[minimized][39m[22m (name: main) 1 related asset
[1m./example.js[39m[22m 70 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
[1m./increment.js[39m[22m 251 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
[1m./math.js[39m[22m 313 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.2 compiled [1m[32msuccessfully[39m[22m
```
