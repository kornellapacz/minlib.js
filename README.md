# minlib.js

Minlib.js is small and simple javascript library to adding event listeners and searching elements by CSS selectors.

file (ES6)    | weight
--------------|-------------
minlib.js     | 0.658 KB
minlib.min.js | **0.245 KB**

## Instalation

Include minlib.min.js on your page before the closing `</body>` tag
```html
<script src="/path/to/minlib.min.js"></script>
```

## Documentation

### query() ([`Element.querySelector()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/querySelector "Element.querySelector() - MDN")) 

Function `query()` returns the first element that is a descendant of the element on which it is invoked that matches the specified group of selectors.

Syntax:`query(selector, baseElement)` 

If a baseElement is document, you don't have to write this.

##### example 1

```javascript
query('h1'); // returns first h1 element (baseElement is document)
```

##### example 2
```javascript
let el = query('.container'); // returns element with class container

query('h1', el);              // returns first h1 element from el (baseElement is el)
```

##### exmaple 3

```javascript
query('header h1');
```

### queryAll() ([`Element.querySelectorAll()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/querySelectorAll "Element.querySelectorAll - MDN"))

Function `queryAll()` returns a Array (not NodeList) of all elements descended from the element on which it is invoked that matches the specified group of CSS selectors. 


Syntax:`queryAll(selector, baseElement)`

In selector you can write:

1. String with selector (example 1)
2. String with selectors (example 2)
3. Element (function returns array with this element)
4. Array with elements (function returns this array)

If a baseElement is document, you don't have to write this.

>`queryAll()` returs Array so you should use[`for...of`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of "for...of - MDN") [(`or forEach()`)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach "Array.prototype.forEach() - MDN")

##### example 1

```javascript
queryAll('h1'); // returns array with all h1 elements (baseElement is document)
```

##### example 2

```javascript
queryAll('h1, p') // returns array with all h1 and p elements 
```

##### example 3

```javascript
queryAll('h1', element); // returns array with all h1 elements from element (baseElement is element)
```

### addEvent() ([`element.addEventListener`](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener "element.addEventListener - MDN") )
 
 Syntax: `addEvt(target,`[`type,`](https://developer.mozilla.org/en-US/docs/Web/Events "Event reference - MDN")`listener, useCapture)`
 
 In target you can write: 
1. [Element ](https://developer.mozilla.org/en-US/docs/Web/API/element "Element - MDN") (or a function that returns an element) (example 3, example 4, example 5, example 6)
1. String with selector (example 1)
2. String with selectors (example 2)
3. Array with elements (example 6)

##### example 1
 
minlib.js:
```javascript
addEvt('h1', 'click', yourFunction); // sets event listener on all h1 element
```

##### example 2

```javascript
addEvent('h1, h2, p', 'click', yourFunction); // sets event listener on all h1 h2 and p element 
```
In [vanilla.js](http://vanilla-js.com/) you have to write:
```javascript
document.querySelectorAll('h1, h2, p').forEach(function (element) {
    element.addEventListener('click', yourFunction);
});
```

##### example 3
```javascript
addEvent(query('#row'), 'click', fuction () {
    //code in anonymous function 
});
```

##### example 4

```javascript
addEvent(queryAll('.button')[1], 'click', yourFunction); // sets event listener on second element with button class
```

##### example 5

```javascript
let el = query('.container');
addEvent(el, 'click', yourFunction);
```

##### example 6

```javascript
let elOne = document.createElement('h1'),
    elTwo = document.createElement('p');
    
addEvent([elOne, elTwo], 'click', yourFunction)
```

##### example 7  

```javascript
let div = document.createElement('div')
addEvent(div, 'click', yourFunction);
```

### loaded() ([`load`](https://developer.mozilla.org/en-US/docs/Web/Events/load "load - MDN"))

function `loaded()` fired when a resource and its dependent resources have finished loading.

Syntax: `loaded(listener)`

##### example

```javascript
loaded(function(){
    //code
});
```

## License

The MIT License (MIT)