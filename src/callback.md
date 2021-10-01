# Callback (call, apply)

* In JavaScript, a callback function is a function that is passed into another function as an argument. This function can then be invoked during the execution of that higher order function (that it is an argument of).

* Since, in JavaScript, functions are objects, functions can be passed as arguments.

```js
const isEven = function(n) {
  return n % 2 == 0;
}
 
cons printMsg = function (evenFunc, num) {
  const isNumEven = evenFunc(num);
  console.log("The number " + num + " is an even number: " + isNumEven + ".")
}
 
// Pass in isEven as the callback function
printMsg(isEven, 4); 
// Prints: The number 4 is an even number: True.
```

Sometimes it is usefull to call function and pass some context to it:
```js
function greet() {
  const reply = [this.animal, 'typically sleep between', this.sleepDuration].join(' ');
  console.log(reply);
}

const obj = {
  animal: 'cats', sleepDuration: '12 and 16 hours'
};

greet.call(obj);

greet.apply(obj);

// What the difference between call and apply?
```
