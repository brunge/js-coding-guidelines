#JavaScript Coding Guidelines

## Index
1. [Encoding](#encoding)
2. Line Length
3. Indentation and Whitespaces
4. Commas
5. Semicolons
6. Comments
7. Variable definition
8. Primitive Literals
9. Operator Spacing and Blocks
10. Object Literals
11. Objects
12. Arrays
13. Strings
14. Properties
15. Type Casting & Coercion


***


## Encoding

Always use UTF-8 encoding for js files.


---


## Line Length

Each line should be no longer than 80 characters. If a line goes longer than 80 characters, it should be wrapped after an operator (comma, plus, etc.). The following line should be indented two levels (eight characters).

(See GitHub: no horizontal scrollbar)

Strings longer than 80 characters should be written across multiple lines using string concatenation. (see 8.Strings ???)


---


## Indentation and Whitespaces

* Always use spaces for indentation in Javascript.
* Use 4 spaces per soft tab (indentation level).
* Place 1 space before the leading brace.
* Place 1 space before the opening parenthesis in control statements (if, while etc.). Place no space before the argument list in function calls and declarations.

```javascript
// bad
if(isJedi) {
  fight ();
}

// good
if (isJedi) {
  fight();
}

// bad
function fight () {
  console.log ('Swooosh!');
}

// good
function fight() {
  console.log('Swooosh!');
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

// bad
var leds = stage.selectAll('.led').data(data).enter().append('svg:svg').classed('led', true)
    .attr('width', (radius + margin) * 2).append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);

// good
var leds = stage.selectAll('.led')
    .data(data)
  .enter().append('svg:svg')
    .classed('led', true)
    .attr('width', (radius + margin) * 2)
  .append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);
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


---


## Commas

Never use leading commas!
And don't use additional trailing comma in objects and arrays!

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


---


## Semicolons

After each statement and add a semicolon!

Yes! Always use semicolons! ???

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


## Primitive Literals

Strings should be in single quotes ( like: ’foo’ )


---


## Comments

Every function should have a comment in JsDoc style format!

Complex code parts should also be commented as inline comment.

(see 2. Line Length)


---


## Variable definition

Always define variables on top of a scope.

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


In a variable definition block, the type of a variable should always be predefined, even if its value is empty. This shows the type of a variable and reserves the correct memory space.

Example:
```javascript
var foo = ‘’,
    bar = [],
    fooBar = {};
```


Avoid single letter names. Be descriptive with your naming.

Use readable synonyms in place of reserved words.

Write meaningful variable names:

```javascript
//Bad
var callback = function(e) {...}

//Good
var mouseMoveHandler = function(e) {...}
```

Name your functions. This is helpful for stack traces. #TBD

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

If your file exports a single class, your filename should be exactly the name of the class.

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


No numeric beginning of variable names (JS Standard)

 ```javascript
$ = jQuery object
_ = private variables
_$ = private jQuery object
```

MyKlass = Constructor and class names should start uppercase (PascalCase)

Use camelCase when naming objects, functions, and instances.
Variable names always camel-cased and should start lowercase

FOOBAR = constant


Use a leading underscore _ when naming private properties.





Should be discussed:

Variables start with type definition prefix like:
 ```javascript
sFoo = “bar”; (String)
aBar = [1, 2, 3]; (Array)
etc.
```

self = this not that! ????
When saving a reference to this use _this ?????


---


## Operator Spacing and Blocks

Operators with two operands must be preceded and followed by a single space to make
the expression clear. Operators include assignments and logical operators.


Use braces with all multi-line blocks.

```javascript
// bad
if(name=='') {
  // ...stuff...
}

// bad
if(name==''){return}


// good
if (name === ’’) {
  retrun;
}
```

If you're using multi-line blocks with if and else, put else on the same line as your if block's closing brace.

```javascript
// bad
if (test) {
  thing1();
  thing2();
}
else {
  thing3();
}

// good
if (test) {
  thing1();
  thing2();
} else {
  thing3();
}
```


---


## Object Literals

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


var myNumbers = [1, 2, 3]
```


---


## Objects

Use the literal syntax for object creation.
```javascript
// bad
var item = new Object();

// good
var item = {};
```

Don't use reserved words as keys. It won't work in IE8. More info.
(http://es5.github.io/#x7.6.1)


```javascript
// bad
var superman = {
  default: { clark: 'kent' },
  private: true
};

// good
var superman = {
  defaults: { clark: 'kent' },
  hidden: true
};
```


---


#### 12. Arrays

Use the literal syntax for array creation.

```javascript
// bad
var items = new Array();

// good
var items = [];
```


---


## Strings

Note: If overused, long strings with concatenation could impact performance. jsPerf & Discussion.

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
].join(‘’);

// good
var errorMessage = 'This is a super long error that was thrown because ' +
  'of Batman. When you stop to think about how Batman had anything to do ' +
  'with this, you would get nowhere fast.';
```


When programmatically building up a string, use Array#join instead of string concatenation. 

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


## Properties


Use dot notation when accessing properties.

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



Use one var declaration per variable. It's easier to add new variable declarations this way, and you never have to worry about swapping out a ; for a , or introducing punctuation-only diffs.

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


Declare unassigned variables last. This is helpful when later on you might need to assign a variable depending on one of the previous assigned variables.

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


---


#### 15. Type Casting & Coercion


Perform type coercion at the beginning of the statement.
Strings:

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


Use parseInt for Numbers and always with a radix for type casting. 

```javascript
var inputValue = '4';

// bad
var val = new Number(inputValue);

// bad
var val = +inputValue;

// bad
var val = inputValue >> 0;

// bad
var val = parseInt(inputValue);

// good
var val = Number(inputValue);

// good
var val = parseInt(inputValue, 10);
```


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




















#TBD:

ES6 Guidelines???


Resources Block???


- return this for chaining
- overwriting prototype object
- naming functions
- getter/setter


Performance related guidelines: ???


Use shortcuts????

```javascript
// bad
if (name !== '') {
  // ...stuff...
}

// good
if (name) {
  // ...stuff...
}

// bad
if (collection.length > 0) {
  // ...stuff...
}

// good
if (collection.length) {
  // ...stuff...
}
```
