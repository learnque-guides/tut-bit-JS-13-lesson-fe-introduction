# setTimeout and setInterval

**setTimeout syntax:**

```js
const timeoutID = setTimeout(function[, delay, arg1, arg2, ...]);
const timeoutID = setTimeout(function[, delay]);
const timeoutID = setTimeout(code[, delay]);
```
The returned timeoutID is a positive integer value which identifies the timer created by the call to setTimeout(). This value can be passed to clearTimeout() to cancel the timeout.


**setInterval syntax:**
```js
const intervalID = setInterval(func, [delay, arg1, arg2, ...]);
const intervalID = setInterval(function[, delay]);
const intervalID = setInterval(code, [delay]);
```

This method returns an interval ID which uniquely identifies the interval, so you can remove it later by calling clearInterval().

*The browser provides setTimeout and setInterval functions that can take string arguments or function arguments. When given string arguments, setTimeout and setInterval act as eval. The string argument form also should be avoided.*
