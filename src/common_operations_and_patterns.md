# Common operations and patterns for DOM

Find Elements

```js
document.querySelectorAll('.my #awesome selector');
```

Find Children

```js
el.querySelectorAll(selector);
```

Filter

```js
Array.prototype.filter.call(document.querySelectorAll(selector), filterFn);
```

Empty (remove childs)

```js
while(el.firstChild) {
   el.removeChild(el.firstChild); 
}
```

Each

```js
var elements = document.querySelectorAll(selector);
Array.prototype.forEach.call(elements, function(el, i){

});
```

Contains

```js
!!el.querySelector(selector);

el !== child && el.contains(child);
```

Clone

```js
el.cloneNode(true);
```

Get children

```js
el.children
```

Inser before

```js
target.insertAdjacentElement('beforebegin', element);
```

Append

```js
parent.appendChild(el);
```

After

```js
target.insertAdjacentElement('afterend', element);
```

Add class

```js
el.classList.add(className);
```

Show or hide

```js
el.style.display = '';
el.style.display = 'none';
```

Fade out

```css
.show {
  opacity: 1;
}
.hide {
  opacity: 0;
  transition: opacity 400ms;
}
```

```js
el.classList.add('hide');
el.classList.remove('show');
```

Fade In

```css
.show {
  transition: opacity 400ms;
}
.hide {
  opacity: 0;
}
```

```js
el.classList.add('show');
el.classList.remove('hide');
```

Get / Remove / Set attribute

```js
el.getAttribute('tabindex');
el.removeAttribute('tabindex');
el.setAttribute('tabindex', 3);
```

Get inner/outer HTML

```js
el.innerHTML
el.outerHTML
```

Get / Set style

```js
getComputedStyle(el)[ruleName];
el.style.borderWidth = '20px';
```

Get width or height

```js
parseFloat(getComputedStyle(el, null).width.replace("px", ""));
parseFloat(getComputedStyle(el, null).height.replace("px", ""));
```

Parent or child

```js
el.parentNode;
el.childNode;
```

Events

```js
el.addEventListener('click', function () {}, false);
el.removeEventListener(eventName, eventHandler);
```

On document ready

```js
function ready(fn) {
  if (document.readyState != 'loading'){
    fn();
  } else {
    document.addEventListener('DOMContentLoaded', fn);
  }
}
```

Trigger event

```js
// For a full list of event types: https://developer.mozilla.org/en-US/docs/Web/API/document.createEvent
let event = document.createEvent('HTMLEvents');
event.initEvent('change', true, false);
el.dispatchEvent(event);

// custom event
if (window.CustomEvent && typeof window.CustomEvent === 'function') {
  var event = new CustomEvent('my-event', {detail: {some: 'data'}});
} else {
  var event = document.createEvent('CustomEvent');
  event.initCustomEvent('my-event', true, true, {some: 'data'});
}

el.dispatchEvent(event);
```

Parse JSON

```js
JSON.parse(string);
```