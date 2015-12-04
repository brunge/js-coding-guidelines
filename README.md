# JavaScript Coding Guidelines

## Index

#### General
[Introduction](#introduction)

1. [Encoding](#encoding)
2. [Javascript Modus](#javascript-modus)
3. [Line Length](#line-length)
4. [Indentation and Whitespaces](#indentation-and-whitespaces)
5. [Comments](#comments)
6. [Commas and Semicolons](#commas-and-semicolons)
7. [Variables](#variables)
8. [Comparison Operators and Equality](#comparison-operators-and-equality)
9. [Operator Spacing and Blocks](#operator-spacing-and-blocks)
10. [Type Casting and Coercion](#type-casting-and-coercion)
11. [Strings](#strings)
12. [Objects](#objects)
13. [Arrays](#arrays)
14. [Properties](#properties)

#### ES6

1. [ES6 Variables](#es6-variables)
2. [ES6 References](#es6-references)
3. [ES6 Destructuring](#es6-destructuring)
4. [ES6 Strings](#es6-strings)
5. [ES6 Functions](#es6-functions)
6. [ES6 Arrow Functions](#es6-arrow-functions)
7. [ES6 Constructors](#es6-constructors)
8. [ES6 Modules](#es6-modules)
9. [ES6 Naming Conventions](#es6-naming-conventions)


## Introduction

This styleguide provides rules and best practices for writing clean, well structured and maintainable code.
It has been created to improve cross-project cooperation and reduce the initial time spent on getting familiar with a new project.

You get a general overview about how to "style" the code followed by some ES6 relevant guidelines.

__Note: For most of the general code examples the ES5 syntax is used. Keep in mind not to mix syntaxes if you write in ES6.__

__This styleguide is obligatory!__ If you are convinced that your project cannot be implemented without violating some of these rules, [please contact us](#persons-in-charge).


# General

## Encoding

* Always use UTF-8 encoding for javascript files.


---


## Javascript Modus

* ES5 and ES6 are triggered by writing `use strict`:

```javascript
//bad + error
"use strict"

//good
'use strict';
```

---


## Line Length

* Each line should be __no longer than 80 characters__. If a line goes longer than 80 characters, it should be wrapped after an operator (comma, plus, etc.). The following line should be indented two levels (eight characters/spaces).

* Strings longer than 80 characters should be written across multiple lines using string concatenation.


---


## Indentation and Whitespaces

* Always use __spaces__ for indentation in Javascript.
* Use __4 spaces per indentation level__ (soft tab).
* Place 1 space before the leading brace.
* Place 1 space before the opening parenthesis in control statements (if, while etc.).
* Place no space before the argument list in function calls and declarations.

```javascript
// bad
if(isJedi){
∙∙fight∙();
}

// bad
if∙(isJedi)∙{∙∙∙
∙∙∙∙fight();∙∙
}∙∙∙∙∙

// good
if∙(isJedi)∙{
∙∙∙∙fight();
}

// bad
function∙fight∙()∙{
∙∙console.log∙('Swooosh!');
}

// good
function∙fight()∙{
∙∙∙∙console.log('Swooosh!');
}
```

* Set off operators with spaces.

```javascript
// bad
var x=y+5;

// good
var x = y + 5;
```

* Use indentation when making long method chains. Use a leading dot, which emphasizes that the line is a method call, not a new statement.

```javascript
// bad
$('#items').find('.selected').highlight().end().find('.open').updateCount();

// bad
$('#items').
    find('.selected').
        highlight().
        end().
    find('.open').
        updateCount();

// good
$('#items')
    .find('.selected')
        .highlight()
    .end()
    .find('.open')
        .updateCount();
```

* Leave a blank line after blocks and before the next statement.

```javascript
// bad
if (foo) {
    return bar;
}
return baz;

// good
if (foo) {
    return bar;
}

return baz;


// bad
var obj = {
    foo: function() {
    },
    bar: function() {
    }
};
return obj;

// good
var obj = {
    foo: function() {
    },

    bar: function() {
    }
};

return obj;
```

* Do not pad your blocks with blank lines.

```javascript
// bad
function bar() {

  console.log(foo);

}

// also bad
if (baz) {

  console.log(qux);
} else {
  console.log(foo);

}

// good
function bar() {
  console.log(foo);
}

// good
if (baz) {
  console.log(qux);
} else {
  console.log(foo);
}
```

---


## Comments

* Every function should have a comment in JsDoc style format. (More Infos: [http://usejsdoc.org](http://usejsdoc.org))

* Complex code parts should also be commented as inline comment. (Beware of [Line Length](#line-length).)


```javascript
/**
* [doCrazyStuff description]
* @param  {[type]} name  [description]
* @param  {[type]} value [description] 
* @return {[type]}       [description]
*/
function doCrazyStuff(name, value) {
    
    // complex codepart description
    while(....) {
        // super crazy stuff
    };
}
```

* Prefixing your comments with `FIXME` or `TODO` helps other developers quickly understand if you're pointing out a problem that needs to be revisited, or if you're suggesting a solution to the problem that needs to be implemented. These are different than regular comments because they are actionable. The actions are FIXME -- need to figure this out or TODO -- need to implement.


---


## Commas and Semicolons

* Never use leading commas.
* Also don't add additional trailing commas in objects and arrays.

```javascript
// bad
var story = [
    once
  , upon
  , aTime
];

// good
var story = [
    once,
    upon,
    aTime
];

// bad
var hero = {
    firstName: 'Bob'
  , lastName: 'Parr'
  , heroName: 'Mr. Incredible'
  , superPower: 'strength'
};

// bad
var hero = {
    firstName: 'Bob',
    lastName: 'Parr',
};

// good
var hero = {
    firstName: 'Bob',
    lastName: 'Parr',
    heroName: 'Mr. Incredible',
    superPower: 'strength'
};
```

* Add semicolons after each statement.


```javascript
// bad
(function() {
    var name = 'Skywalker'
    return name
})()

// good
(function() {
    var name = 'Skywalker';
    return name;
})();
```


---


## Variables

* Always define variables on top of a scope.

```javascript
// bad
function() {
    test();
    console.log('doing stuff..');

    //..other stuff..

    var name = getName();

    if (name === 'test') {
        return false;
    }

    return name;
}

// good
function() {
    var name = getName();

    test();
    console.log('doing stuff..');

    //..other stuff..

    if (name === 'test') {
        return false;
    }

    return name;
}
```

* Use one var declaration per variable. It's easier to add new variable declarations this way, and you never have to worry about swapping out a ; for a , or introducing punctuation-only diffs.


```javascript
// bad
var items = getItems(),
    goSportsTeam = true,
    dragonball = 'z';

// bad
// (compare to above, and try to spot the mistake)
var items = getItems(),
    goSportsTeam = true;
    dragonball = 'z';

// good
var items = getItems();
var goSportsTeam = true;
var dragonball = 'z';
```

* Declare unassigned variables last. This is helpful when later on you might need to assign a variable depending on one of the previous assigned variables.

```javascript
// bad
var i, len, dragonball,
    items = getItems(),
    goSportsTeam = true;

// bad
var i;
var items = getItems();
var dragonball;
var goSportsTeam = true;
var len;

// good
var items = getItems();
var goSportsTeam = true;
var dragonball;
var length;
var i;
```

* Use camelCase when naming variables, objects, functions, and instances. (Starting lowercase.)

* Constructors and class names will be written in PascalCase.

```javascript
var MyKlass = function() {};
```

* Constants will always be uppercase. Use `_` to separate words in constants.

```javascript
// bad
var pi = 3.141592654;

// good
var PI = 3.141592654; // shows that the variable shouldn't be changed

// good
var PI_PA_PO = 3.141592654;

// good in ES6
const pi = 3.141592654;
```

* Always use `const`, `let`, `var` to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace.

* Use `$` for jQuery variables.

```javascript
$myElement = $('.myElement');
```

* Use `_` for naming private variables.

```javascript
_superSecretNumber = 42;
```

* Use `_$` for private jQuery variables.

```javascript
_$superSecretElement = $('.topSecret');
```

* No numeric beginning of variable names.

> It's javascript standard and will result in an syntax error.

```javascript
// bad
var 23bad = 23;
```

* In a variable definition block, the type of a variable should always be predefined, even if its value is empty. This shows the type of a variable and reserves the correct memory space.

```javascript
var foo = '';
var bar = [];
var fooBar = {};
var $fooBar = {}; // jQuery
var $fooBar = $(); // empty jQuery Object 
```

* Avoid single letter names. Be descriptive with your naming and write meaningful variable names.

```javascript
//Bad
var callback = function(e) {...}

//Good
var mouseMoveHandler = function(e) {...}
```

* Use readable synonyms in place of reserved words.


#### Variable definition

* Name your functions. This is helpful for stack traces.

```javascript
// bad
var log = function(msg) {
    console.log(msg);
};

// good
var log = function log(msg) {
    console.log(msg);
};
```


* Never declare a function in a non-function block (if, for, while, etc). Assign the function to a variable instead. Browsers will allow you to do it, but they all interpret it differently, which is bad news bears.



* Never use the Function constructor to create a new function.

> Why? Creating a function in this way evaluates a string similarly to eval(), which opens vulnerabilities.

```javascript
// bad
var add = new Function('a', 'b', 'return a + b');

// still bad
var subtract = Function('a', 'b', 'return a - b');
```



#### Primitive Literals

Primitives are:

* string
* number
* boolean
* null
* undefined


Strings should be defined in single quotes.

```javascript
//bad
var message = "hello";

//good
var message = 'hello';
```

---

## Comparison Operators and Equality

* Use `===` and `!==` over `==` and `!=`.

---

## Operator Spacing and Blocks

* Operators with two operands must be preceded and followed by a single space to make the expression clear. Operators include assignments and logical operators.

* Use braces with all multi-line blocks.

```javascript
// bad
if (test)
  return false;

// good
if (test) {
  return false;
}
```
*  If you're using multi-line blocks with if and else, put else on the same line as your if block's closing brace.

```javascript
// bad
if (test) {
  thing1();
}
else {
  thing2();
}

// good
if (test) {
  thing1();
} else {
  thing2();
}
```

---

## Type Casting and Coercion


* Perform type coercion at the beginning of the statement. Strings:

```javascript
//  => this.reviewScore = 9;

// bad
var totalScore = this.reviewScore + '';

// good
var totalScore = '' + this.reviewScore;

// bad
var totalScore = '' + this.reviewScore + ' total score';

// good
var totalScore = this.reviewScore + ' total score'; 
```


* Use parseInt for Numbers and always with a radix for type casting. 

```javascript
var inputValue = '4';

// bad
var val = new Number(inputValue);

// bad
var val = inputValue >> 0;

// bad
var val = parseInt(inputValue);

// good
var val = Number(inputValue);

// good
var val = parseInt(inputValue, 10);

// good - faster lookup as parseInt is part of window 
var val = +inputValue;
```

* Don't use bit operators!

> Why? Too many internal 64 bit to 32 bit (and reverse) convertions.


Booleans:

```javascript
var age = 0;

// bad
var hasAge = new Boolean(age);

// good
var hasAge = Boolean(age);

// good
var hasAge = !!age;
```

---

## Strings

* Note: If overused, long strings with concatenation could impact performance.

```javascript
// bad
var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// bad
var errorMessage = 'This is a super long error that was thrown because \
of Batman. When you stop to think about how Batman had anything to do \
with this, you would get nowhere \
fast.';

//bad – but good practice if you don’t use uglify
var errorMessage = [
    'This is a super long error that was thrown because ',
    'of Batman. When you stop to think about how Batman had anything to do ',
    'with this, you would get nowhere fast.'
].join('');

// good
var errorMessage = 'This is a super long error that was thrown because ' +
    'of Batman. When you stop to think about how Batman had anything to do ' +
    'with this, you would get nowhere fast.';
```


* When programmatically building up a string, use Array#join instead of string concatenation. 

```javascript
var items;
var messages;
var length;
var i;

messages = [{
    state: 'success',
    message: 'This one worked.'
}, {
    state: 'success',
    message: 'This one worked as well.'
}, {
    state: 'error',
    message: 'This one did not work.'
}];

length = messages.length;

// bad
function inbox(messages) {
    items = '<ul>';

    for (i = 0; i < length; i++) {
        items += '<li>' + messages[i].message + '</li>';
    }

    return items + '</ul>';
}

// good
function inbox(messages) {
    items = [];

    for (i = 0; i < length; i++) {
        // use direct assignment in this case because we're micro-optimizing.
        items[i] = '<li>' + messages[i].message + '</li>';
    }

    return '<ul>' + items.join('') + '</ul>';
}
```

---

## Objects

* Use the literal syntax for object creation.

```javascript
// bad
var item = new Object();

// good
var item = {};
```

* Don't use reserved words as keys. It won't work in IE8. (More info: http://es5.github.io/#x7.6.1)


```javascript
// bad
var superman = {
	    default: {
	        clark: 'kent'
	    },
	    private: true
	};

// good
var superman = {
	    defaults: {
	        clark: 'kent'
	    },
	    hidden: true
	};
```

#### Object Literals

Object literals should have the following format:

*	The opening brace should be on the same line as the containing statement.
*	Each property-value pair should be indented one level with the first property appearing on the next line after the opening brace.
*	Each property-value pair should have an unquoted property name, followed by a colon (no space preceding it), followed by the value.
If the value is a function, it should wrap under the property name (and should have a blank line both before and after the function.)
*	Additional empty lines may be inserted to group related properties or otherwise
improve readability.
*	The closing brace should be on a separate line.

```javascript
// Good
var object = {
        key1: value1,
        key2: value2,
        func: function() {
            // do something
        },
        key3: value3
	};


var myNumbers = [1, 2, 3];
```


---


## Arrays

* Use the literal syntax for array creation.

```javascript
// bad
var items = new Array();

// good
var items = [];

// good
var items = [1, 2, ''];
```

* Use Array#push instead of direct assignment to add items to an array.

```javascript
var someStack = [];

// bad
someStack[someStack.length] = 'abracadabra';

// good
someStack.push('abracadabra');
```


---


## Properties


* Use dot notation when accessing properties.

```javascript
var luke = {
    jedi: true,
    age: 28
};

// bad
var isJedi = luke['jedi'];

// good
var isJedi = luke.jedi;
```


---

<!--## Accessability (ARIA)-->


***

# ES6


## ES6 Variables

* Group all your consts and then group all your lets.

> Why? This is helpful when later on you might need to assign a variable depending on one of the previous assigned variables.

```javascript
// bad
let i, len, dragonball,
	 items = getItems(),
	 goSportsTeam = true;

// bad
let i;
const items = getItems();
let dragonball;
const goSportsTeam = true;
let len;

// good
const goSportsTeam = true;
const items = getItems();
let dragonball;
let i;
let length;
```

#### Variable definition

* If your file exports a single class, your filename should be exactly the name of the class.

```javascript
// file contents
class CheckBox {
    // ...
}
module.exports = CheckBox;

// in some other file
// bad
var CheckBox = require('./checkBox');

// bad
var CheckBox = require('./check_box');

// good
var CheckBox = require('./CheckBox');
```

---


## ES6 References

* Use `const` for all of your references; avoid using `var`.

```javascript
// bad
var a = 1;
var b = 2;

// good
const a = 1;
const b = 2;
```

* If you must reassign references, use `let` instead of `var`.

```javascript
// bad
var count = 1;
if (true) {
	count += 1;
}

// good, use the let.
let count = 1;
if (true) {
	count += 1;
}

// good
for (let a = 0, b = 10; a < b; a++) {
	// let makes 'a' and 'b' only exist inside the for loop
}
```

* Use property value shorthand.

> Why? It is shorter to write and descriptive.

```javascript
const lukeSkywalker = 'Luke Skywalker';

// bad
const obj = {
	lukeSkywalker: lukeSkywalker,
};

// good
const obj = {
	lukeSkywalker,
};
```

* Group your shorthand properties at the beginning of your object declaration.

> Why? It's easier to tell which properties are using the shorthand.

```javascript
const anakinSkywalker = 'Anakin Skywalker';
const lukeSkywalker = 'Luke Skywalker';

// bad
const obj = {
	episodeOne: 1,
	twoJediWalkIntoACantina: 2,
	lukeSkywalker,
	episodeThree: 3,
	mayTheFourth: 4,
	anakinSkywalker,
};

// good
const obj = {
	lukeSkywalker,
	anakinSkywalker,
	episodeOne: 1,
	twoJediWalkIntoACantina: 2,
	episodeThree: 3,
	mayTheFourth: 4,
};
```

---

## ES6 Destructuring

* Use object destructuring when accessing and using multiple properties of an object.

> Why? Destructuring saves you from creating temporary references for those properties.

```javascript
// bad
function getFullName(user) {
	const firstName = user.firstName;
	const lastName = user.lastName;
	
	return `${firstName} ${lastName}`;
}

// good
function getFullName(obj) {
	const { firstName, lastName } = obj;
	return `${firstName} ${lastName}`;
}

// best
function getFullName({ firstName, lastName }) {
	return `${firstName} ${lastName}`;
}
```

* Use array destructuring.


```javascript
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
```


* Use object destructuring for multiple return values, not array destructuring.

> Why? You can add new properties over time or change the order of things without breaking call sites.


```javascript
// bad
function processInput(input) {
	// then a miracle occurs
	return [left, right, top, bottom];
}

// the caller needs to think about the order of return data
const [left, __, top] = processInput(input);

// good
function processInput(input) {
	// then a miracle occurs
	return { left, right, top, bottom };
}

// the caller selects only the data they need
const { left, right } = processInput(input);
```

---


## ES6 Strings

* When programmatically building up strings, use template strings instead of concatenation.

> Why? Template strings give you a readable, concise syntax with proper newlines and string interpolation features.

```javascript
// bad
function sayHi(name) {
	return 'How are you, ' + name + '?';
}

// bad
function sayHi(name) {
	return ['How are you, ', name, '?'].join();
}

// good
function sayHi(name) {
	return `How are you, ${name}?`;
}
```

* Use backticks to write multi-line strings.

```javascript
var longString = `Then took the other, as just as fair,
    And having perhaps the better claim
    Because it was grassy and wanted wear,
    Though as for that the passing there
    Had worn them really about the same ...`
```

---

## ES6 Functions

* Use default parameter syntax rather than mutating function arguments.

```javascript
// bad
function handleThings(opts) {
	opts = opts || {};
	// ...
}

// bad
function handleThings(opts) {
	if (opts === void 0) {
		opts = {};
	}
	// ...
}

// good
function handleThings(opts = {}) {
	// ...
}
```


* Always put default parameters last.

```javascript
// bad
function handleThings(opts = {}, name) {
	 // ...
}

// good
function handleThings(name, opts = {}) {
	// ...
}
```

---

## ES6 Arrow Functions

* When you must use function expressions (as when passing an anonymous function), use arrow function notation.

> Why? It creates a version of the function that executes in the context of this, which is usually what you want, and is a more concise syntax.

> Why not? If you have a fairly complicated function, you might move that logic out into its own function declaration.

```javascript
// bad
[1, 2, 3].map(function (x) {
	const y = x + 1;
	return x * y;
});

// good
[1, 2, 3].map((x) => {
	const y = x + 1;
	return x * y;
});
```

* In case the expression spans over multiple lines, wrap it in parentheses for better readability.

> Why? It shows clearly where the function starts and ends.
 
```javascript
// bad
[1, 2, 3].map(number => 'As time went by, the string containing the ' +
	`${number} became much longer. So we needed to break it over multiple ` +
	'lines.'
);

// good
[1, 2, 3].map(number => (
	`As time went by, the string containing the ${number} became much ` +
	'longer. So we needed to break it over multiple lines.'
));
```

If your function only takes a single argument, feel free to omit the parentheses.

> Why? Less visual clutter.
eslint rules: arrow-parens.

```javascript
// good
[1, 2, 3].map(x => x * x);

// good
[1, 2, 3].reduce((y, x) => x + y);
```

---

## ES6 Constructors

* Always use class. Avoid manipulating prototype directly.

> Why? class syntax is more concise and easier to reason about.
  
```javascript
// bad
function Queue(contents = []) {
	this._queue = [...contents];
}
Queue.prototype.pop = function () {
	const value = this._queue[0];
	this._queue.splice(0, 1);
	return value;
}

// good
class Queue {
	constructor(contents = []) {
  		this._queue = [...contents];
	}
	pop() {
  		const value = this._queue[0];
  		this._queue.splice(0, 1);
  		return value;
	}
}
```

* Use extends for inheritance.

> Why? It is a built-in way to inherit prototype functionality without breaking instanceof.
 
```javascript
// bad
	const inherits = require('inherits');
	function PeekableQueue(contents) {
	Queue.apply(this, contents);
}
inherits(PeekableQueue, Queue);
PeekableQueue.prototype.peek = function () {
	return this._queue[0];
}

// good
class PeekableQueue extends Queue {
	peek() {
  		return this._queue[0];
	}
}
```

* Methods can return this to help with method chaining.

```javascript
// bad
Jedi.prototype.jump = function () {
	this.jumping = true;
 	return true;
};

Jedi.prototype.setHeight = function (height) {
	this.height = height;
};

const luke = new Jedi();
luke.jump(); // => true
luke.setHeight(20); // => undefined

// good
class Jedi {
	jump() {
		this.jumping = true;
		return this;
	}

	setHeight(height) {
		this.height = height;
		return this;
	}
}

const luke = new Jedi();

luke.jump()
	.setHeight(20);
```

---

## ES6 Modules

* Always use modules (`import`/`export`) over a non-standard module system. You can always transpile to your preferred module system.

> Why? Modules are the future, let's start using the future now.

```javascript
// bad
const MyModule = require('./MyModule');
module.exports = MyModule.batman;

// ok
import MyModule from './MyModule';
export default MyModule.batman;

// best
import { batman } from './MyModule';
export default batman;
```

* Do not use wildcard imports.

> Why? This makes sure you have a single default export.

```javascript
// bad
import * as MyModule from './MyModule';

// good
import MyModule from './MyModule';
```

* And do not export directly from an import.

> Why? Although the one-liner is concise, having one clear way to import and one clear way to export makes things consistent.

```javascript
// bad
// filename batman.js
export { batman as default } from './MyModule';

// good
// filename batman.js
import { batman } from './MyModule';
export default batman;
```

---

## ES6 Naming Convetions

___See also general section!___

* Use camelCase when you export-default a function. Your filename should be identical to your function's name.

```javascript
function makeStyleGuide() {
}

export default makeStyleGuide;
```

* Use PascalCase when you export a singleton / function library / bare object.

```javascript
const MyModule = {
	batman: {
	}
};


export default MyModule;
```



---

## Persons in charge
__SASS / CSS:__

- [Andy Gutsche (HL)](mailto: andy.gutsche@aperto.com)
- [Marlene Schertler](mailto: marlene.schertler@aperto.com)

__Markup / Accessibility:__

- [Felix Berger](mailto: felix.berger@aperto.com)
- [Wibke Jaeger](mailto: wibke.jaeger@aperto.com)

__JavaScript:__

- [Peter Dematte](mailto: peter.dematte@aperto.com)
- [Bastian Runge](mailto: bastian.runge@aperto.com)



***

## Resources

**Learning ES6**

  - [Draft ECMA 2015 (ES6) Spec](https://people.mozilla.org/~jorendorff/es6-draft.html)
  - [ExploringJS](http://exploringjs.com/)
  - [ES6 Compatibility Table](https://kangax.github.io/compat-table/es6/)
  - [Comprehensive Overview of ES6 Features](http://es6-features.org/)

**Read This**

  - [Standard ECMA-262](http://www.ecma-international.org/ecma-262/6.0/index.html)

**Tools**

  - Code Style Linters
    + [ESlint](http://eslint.org/) - [Airbnb Style .eslintrc](https://github.com/airbnb/javascript/blob/master/linters/.eslintrc)
    + [JSHint](http://www.jshint.com/) - [Airbnb Style .jshintrc](https://github.com/airbnb/javascript/blob/master/linters/jshintrc)
    + [JSCS](https://github.com/jscs-dev/node-jscs) - [Airbnb Style Preset](https://github.com/jscs-dev/node-jscs/blob/master/presets/airbnb.json)

**Other Styles**

  - [Naming this in nested functions](https://gist.github.com/4135065) - Christian Johansen
  - [Conditional Callbacks](https://github.com/airbnb/javascript/issues/52) - Ross Allen
  - [Popular JavaScript Coding Conventions on Github](http://sideeffect.kr/popularconvention/#javascript) - JeongHoon Byun
  - [Multiple var statements in JavaScript, not superfluous](http://benalman.com/news/2012/05/multiple-var-statements-javascript/) - Ben Alman

**Further Reading**

  - [Understanding JavaScript Closures](http://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/) - Angus Croll
  - [Basic JavaScript for the impatient programmer](http://www.2ality.com/2013/06/basic-javascript.html) - Dr. Axel Rauschmayer
  - [You Might Not Need jQuery](http://youmightnotneedjquery.com/) - Zack Bloom & Adam Schwartz
  - [ES6 Features](https://github.com/lukehoban/es6features) - Luke Hoban
  - [Frontend Guidelines](https://github.com/bendc/frontend-guidelines) - Benjamin De Cock

**Books**

  - [JavaScript: The Good Parts](http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742) - Douglas Crockford
  - [JavaScript Patterns](http://www.amazon.com/JavaScript-Patterns-Stoyan-Stefanov/dp/0596806752) - Stoyan Stefanov
  - [Pro JavaScript Design Patterns](http://www.amazon.com/JavaScript-Design-Patterns-Recipes-Problem-Solution/dp/159059908X)  - Ross Harmes and Dustin Diaz
  - [High Performance Web Sites: Essential Knowledge for Front-End Engineers](http://www.amazon.com/High-Performance-Web-Sites-Essential/dp/0596529309) - Steve Souders
  - [Maintainable JavaScript](http://www.amazon.com/Maintainable-JavaScript-Nicholas-C-Zakas/dp/1449327680) - Nicholas C. Zakas
  - [JavaScript Web Applications](http://www.amazon.com/JavaScript-Web-Applications-Alex-MacCaw/dp/144930351X) - Alex MacCaw
  - [Pro JavaScript Techniques](http://www.amazon.com/Pro-JavaScript-Techniques-John-Resig/dp/1590597273) - John Resig
  - [Smashing Node.js: JavaScript Everywhere](http://www.amazon.com/Smashing-Node-js-JavaScript-Everywhere-Magazine/dp/1119962595) - Guillermo Rauch
  - [Secrets of the JavaScript Ninja](http://www.amazon.com/Secrets-JavaScript-Ninja-John-Resig/dp/193398869X) - John Resig and Bear Bibeault
  - [Human JavaScript](http://humanjavascript.com/) - Henrik Joreteg
  - [Superhero.js](http://superherojs.com/) - Kim Joar Bekkelund, Mads Mobæk, & Olav Bjorkoy
  - [JSBooks](http://jsbooks.revolunet.com/) - Julien Bouquillon
  - [Third Party JavaScript](http://manning.com/vinegar/) - Ben Vinegar and Anton Kovalyov
  - [Effective JavaScript: 68 Specific Ways to Harness the Power of JavaScript](http://amzn.com/0321812182) - David Herman
  - [Eloquent JavaScript](http://eloquentjavascript.net/) - Marijn Haverbeke
  - [You Don't Know JS: ES6 & Beyond](http://shop.oreilly.com/product/0636920033769.do) - Kyle Simpson

**Blogs**

  - [DailyJS](http://dailyjs.com/)
  - [JavaScript Weekly](http://javascriptweekly.com/)
  - [JavaScript, JavaScript...](http://javascriptweblog.wordpress.com/)
  - [Bocoup Weblog](http://weblog.bocoup.com/)
  - [Adequately Good](http://www.adequatelygood.com/)
  - [NCZOnline](http://www.nczonline.net/)
  - [Perfection Kills](http://perfectionkills.com/)
  - [Ben Alman](http://benalman.com/)
  - [Dmitry Baranovskiy](http://dmitry.baranovskiy.com/)
  - [Dustin Diaz](http://dustindiaz.com/)
  - [nettuts](http://net.tutsplus.com/?s=javascript)

**Podcasts**

  - [JavaScript Jabber](http://devchat.tv/js-jabber/)

