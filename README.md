#JavaScript Coding Guidelines

## Index
1. Encoding
2. Line Length
3. Indentation and Whitespaces
4. Commas
5. Semicolons
6. Primitive Literals
7. Operator Spacing and Blocks
8. Object Literals
9. Comments
10. Variable definition
11. Objects
12. Arrays
13. Strings
14. Properties
15. Type Casting & Coercion





#### 1. Encoding

Always use UTF-8 encoding for js files.


#### 2. Line Length

Each line should be no longer than 80 characters. If a line goes longer than 80 characters, it should be wrapped after an operator (comma, plus, etc.). The following line should be indented two levels (eight characters).

(See GitHub: no horizontal scrollbar)

Strings longer than 80 characters should be written across multiple lines using string concatenation. (see 8.Strings ???)


#### 3. Indentation and Whitespaces

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


#### 4. Commas

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

#### 5. Semicolons

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



#### 6. Primitive Literals

Strings should be in single quotes ( like: ’foo’ )


#### 7. Operator Spacing and Blocks

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




#### 8. Object Literals

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


#### 9. Comments

Every function should have a comment in JsDoc style format!

Complex code parts should also be commented as inline comment.

(see 2. Line Length)



#### 10. Variable definition

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

Name your functions. This is helpful for stack traces.

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


#### 11. Objects

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



#### 12. Arrays

Use the literal syntax for array creation.

```javascript
// bad
var items = new Array();

// good
var items = [];
```



#### 13. Strings

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



#### 14. Properties


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





















##TBD:


Performance related guidelines:


Use shortcuts.
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
