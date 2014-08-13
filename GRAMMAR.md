# Grammar

## Arguments

The use of `arguments.caller` and `arguments.callee` are prohibited. Both `.caller` and `.callee` make quite a few optimizations impossible so they were deprecated in future versions of JavaScript. In fact, ECMAScript 5 forbids the use of `arguments.callee` in strict mode.

## Arrays/Objects

Short array/object syntax should be used.

```javascript
// Bad
var a = new Array();
var b = new Object();

// Good
var a = [];
var b = {};
```

If any array elements have their own line, they all should. Avoid inconsistency where some are on the same line and others are not.

```javascript
// Bad
var hash = {'Key1' => 'Value',
            'Key2' => 'Value',
            'Key3' => 'Value'};

// Bad
var hash = {'Key1' => 'Value',
    'Key2' => 'Value',
    'Key3' => 'Value'};
```

## Assignments in Conditionals

It can be very confusing for developers who think you have a typo (i.e. they assume you meant `==`, when you intentionally meant `=`). More often than not, code like `if (a = 10) {}` is a typo. However, it can be useful in cases like this one:

```javascript
for (var i = 0, person; person = people[i]; i++) {}
```

Instead, you should wrap these assignments inside parentheses.

```javascript
for (var i = 0, person; (person = people[i]); i++) {}
```

## Bitwise Operators

Do not use bitwise operators such as `^` (XOR), `|` (OR) and others. Bitwise operators are very rare in JavaScript programs and quite often `&` is simply a mistyped `&&`.

## Braces

All control structures use braces, even if they’re optional.

  ```javascript
  var abc;

  // Bad
  if (condition) abc = 'abc';

  // Bad
  if (condition)
      abc = 'abc';

  // Good
  if (condition) {
      abc = 'abc';
  }
  ```

In some circumstances, a lack of braces can lead to bugs (you'd think that `sleep()` is a part of the loop while in reality it is not):

```javascript
while (day)
  shuffle();
  sleep();
```

## Casing

All variable names should use either `camelCase` style or `UPPER_CASE` with underscores (for "constants").

## Commas

Commas belong at the end of the line, obviously. Anything else is the devil.

```javascript
// Good
var obj = {
    name: 'Anton',
    handle: 'valueof',
    role: 'SW Engineer'
};

// Bad
var obj = {
    name: 'Anton'
  , handle: 'valueof'
  , role: 'SW Engineer'
};
```

## Comments

Non-documentation comments are strongly encouraged. A general rule of thumb is that if you look at a section of code and think "Wow, I don't want to try and describe that", you need to comment it before you forget how it works.

C-style comments (`/* */`) and standard C++ comments (`//`) are both fine.

For readability, add a single space after `//` style comments, and an extra space immediately inside both ends of a `/* */`-style comment.

```javascript
// Encouraged Comment
/* Encouraged Comment */

//Discouraged Comment
/*Discouraged Comment*/
```

If you are making a longer, multi-line comment, use line breaks instead of spaces immediately inside both ends of a `/* */`-style comment. The content may, at your option, be indented as well.

```javascript
/*
    This is an extra long comment that I'm breaking up
    into multiple lines for improved readability.
*/
```

There should always be one line of whitespace above the start of a comment block.

```javascript
// This is my code.
console.log('This is my code.');

// This is more code.
console.log('This is more code.');

if (condition) {
    // comment
    console.log('code');
}
```

## Constructors

Capitalizing names of constructor functions is required. Capitalizing functions that are intended to be used with new operator is just a convention that helps programmers to visually distinguish constructor functions from other types of functions to help spot mistakes when using this.

Not doing so won't break your code in any browsers or environments but it will be a bit harder to figure out -- by reading the code -- if the function was supposed to be used with or without `new`. And this is important because when the function that was intended to be used with `new` is used without it, this will point to the global object instead of a new object.

```javascript
var a = new MyConstructor();
```

Also, the use of constructor functions for side-effects is prohibited. Some people like to call constructor functions without assigning its result to any variable. There is no advantage in this approach over simply calling `MyConstructor` since the object that the operator `new` creates isn't used anywhere so you should generally avoid constructors like this one.

```javascript
new MyConstructor();
```

## Control Structures

Control structure keywords MUST have one space after them; method and function calls MUST NOT.

  ```javascript
  if () {}
  else () {}
  function example() {}
  var example = function() {}
  ```

Opening parentheses for control structures MUST NOT have a space after them, and closing parentheses for control structures MUST NOT have a space before.

  ```javascript
  if ("abc" === abc) {}
  ```

## Encapsulation

No global variables. ಠ_ಠ

All code should be properly encapculated, and only expose the things that need to be available under a project namespace of some sort. (We don't want to pollute the global scope.)

  ```javascript
  ;(function() {
      if (typeof window.MyNamespace === 'undefined') {
          window.MyNamespace = {};
      }

      window.MyNamespace.myMethod = function() {
          // ...
      };
  })();
  ```

Code should be componentized. For example, a single widget should be self-contained. There should not be multiple "ideas" per file.

## Eval

No. ಠ_ಠ

## Expressions

When the value of a variable is the result of an expression, wrap the expression in parentheses. This adds clarity and enhances readability.

```javascript
var formatTime = function(seconds) {
    var hour, mod, hh, md, mm;

    hh = (Math.floor(seconds / 60));
    md = ((hh > 11) ? 'PM' : 'AM');
    hh = ((hour = hh % 12) ? hour : 12);
    mm = ((mod = (seconds % 60)) < 10 ? '0' + mod : mod);

    return [hh, mm, md];
};
```

## File Management

* Files MUST use only UTF-8 without BOM for JavaScript code.

* An empty line feed should precede a return statement.

* Remove trailing whitespace at the end of lines.

* A file must always end with an empty line feed.

* Line-endings should use the `\n` character (`LF`) used by default on Mac OS X and *nix systems. Windows uses `\r\n` (`CRLF`) by default, so make sure that your IDE saves files with Unix-flavored line-endings.

## for-in

All `for in` loops are required to filter an object's items.

The `for in` statement allows for looping through the names of all of the properties of an object including those inherited throught the prototype chain. This behavior can lead to unexpected items in your object so it is generally safer to always filter inherited properties out as shown in the example:

```javascript
for (key in obj) {
    if (obj.hasOwnProperty(key)) {
        // We are sure that obj[key] belongs to the object and was not inherited.
    }
}
```

For more in-depth understanding of `for in` loops in JavaScript, read [Exploring JavaScript for-in loops](http://javascriptweblog.wordpress.com/2011/01/04/exploring-javascript-for-in-loops/) by Angus Croll.

## Function Invocations

The use of immediate function invocations without wrapping them in parentheses is prohibited. Wrapping parentheses assists readers of your code in understanding that the expression is the result of a function, and not the function itself.

```javascript
// Good
(function() {
    // ...
})();

// Bad
function() {
    // ...
}();
```

## Functions in Loops

As a general rule, don't ever create functions inside of loops. 99% of the time, I will slap you across the face and call you stupid. You are trying to be too damn clever and it simply won't work. It can lead to bugs like this.

```javascript
var nums = [];

for (var i = 0; i < 10; i++) {
    nums[i] = function (j) {
        return i + j;
    };
}

nums[0](2); // Prints 12 instead of 2
```

In the _very rare_ case where there is sanity in this approach, to fix the code above you need to pass the value of `i` into the function's scope instead of allowing the variable scope to leak.

```javascript
var nums = [];

for (var i = 0; i < 10; i++) {
    (function (i) {
        nums[i] = function (j) {
            return i + j;
        };
    }(i));
}
```

## Increment/Decrement Operators

You are encouraged to give increment/decrement operators (`++` and `--`) a line of their own for the simple purpose of clarity (with the exception of `for` loops).

```javascript
// Discouraged
foo[i++] = j;
foo[--j] = i;

// Encouraged
foo[i] = j;
i++;

j--;
foo[j] = i;
```

## Indenting

Code MUST use 4 spaces for indenting, not tabs. (They'll all get munged once they're compiled anyway.)

## `__iterator__`

This property is not supported by all browsers so you should avoid it.

## `javascript:` Protocol

Forget the `javascript:` protocol ever existed. Never use it. For anything. Ever. _Especially_ on the front-end.

There are far more enlightened ways of doing clever things with clicks and events on the front-end. Using the `javascript:` protocol is not one of them.

## Integers

When using `parseInt()`, always pass the `base` value as the second parameter. Normally this is `10`, but it can be others as well. I've seen `'08'` be converted into unexpected values when the browser had to guess what the base number system was.

```javascript
// Bad
var myInt = parseInt('0A'); // 0, in decimal

// Good
var myInt = parseInt('0A', 16); // 10, in hexadecimal
```

## Memoization

Cache your re-usable calculations whenever possible. This is _especially_ important for `for` loops and jQuery DOM selectors. Unlike in other languages, the JavaScript engine does NOT do this for you.

```javascript
// Bad
var a = new Array(1000000);
for (var i = 0; i < a.length; i++) {}

// Good
var a = new Array(1000000);
for (var i = 0, max = a.length; i < max; i++) {}
```

## Mime Type

If your code is intended to support modern browsers, use `application/javascript`, as per [RFC-4329 §7](http://tools.ietf.org/html/rfc4329#section-7). If you need to support a version of Internet Explorer earlier than 9.0, you must instead use the obsoleted `text/javascript`.

  ```html
  <script type="application/javascript">
      // ...
  </script>
  ```

## Multi-line Strings

Multi-line strings can be dangerous in JavaScript because all hell breaks loose if you accidentally put a whitespace in between the escape character (`\`) and a new line.

```javascript
var text = "Hello\
World"; // All good.

text = "Hello
World"; // No escape character!

text = "Hello\
World"; // There is a space after `\`!
```

It is preferred to avoid them and concatenate across lines instead.

## Naming

* Variables are `camelCase`.

* Constants are always `ALL_CAPS`.

* Classes should be called `StudlyCase`.

* Namespaces and classes should all prefer singular names.

  ```javascript
  MyNamespace.Util.Dom
  MyNamespace.Util.Event
  MyNamespace.Widget.TableSorter
  ```

* There's no hard and fast rule when it comes to the length of a name, so just try and be as concise as possible without affecting clarity too much.

## Object Notation

Using "dot" notation (e.g., `person.name`) to refer to nodes in an object is greatly preferred over using array notation (e.g., `person['name']`).

This also implies that it is preferred to use object keys which can be used with dot notation. In cases where this is unavoidable (e.g., someone used `person['first-name']` and now you're stuck with it) array notation is allowed.

## Prototype Extension

Overwriting prototypes of native objects such as `Array`, `Date` and so on, is prohibited.

```javascript
Array.prototype.count = function (value) {
    return 4;
};
```

## Semicolons

Despite the fact that semicolons are not explicitly required all the time, please include them anyway -- unless you really, really know that excluding them is safe.

For more information about semicolons in JavaScript read [An Open Letter to JavaScript Leaders Regarding Semicolons](http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding) by Isaac Schlueter and [JavaScript Semicolon Insertion](http://inimino.org/~inimino/blog/javascript_semicolons).

## Spelling

If there is ever a discrepancy between English-speaking dialects, use **U.S. English** as a baseline for both spelling and word choice. [Grammarist](http://grammarist.com/spelling/) and similar websites can help ensure intended usage.

```
color (correct)
colour (incorrect)

spelled (correct)
spelt (incorrect)

canceled (correct)
cancelled (incorrect)

labeled (correct)
labelled (incorrect)

math (correct)
maths (incorrect)

apartment (correct)
flat (incorrect)

"Apple is very successful." (correct)
"Apple are very successful." (incorrect)
```

## Strict Mode

"Strict mode" is a way to opt-in to a restricted variant of JavaScript. Strict mode eliminates some JavaScript pitfalls that didn't cause errors by changing them to produce errors. It also fixes mistakes that made it difficult for the JavaScript engines to perform certain optimizations.

```javascript
"use strict";
```

Strict mode should be applied for function scope **only**, which is fine since you're encapsulating all of your JavaScript code inside of an anonymous function&hellip; right?

## Strings

Strings should be double quoted, as they are required to be for spec-compliant [JSON](http://json.org).

## switch-case

* The contents of each `case` or `default` block should be indented for readability. This includes the closing `break`.

* There should always be a `default` block.

* You are encouraged to add additional line breaks for improved readability.

```javascript
switch (value) {
    case 'a':
        console.log('a');
        break;

    case 'b':
        console.log('b');
        break;

    default:
        console.log('z');
        break;
}
```


## Ternary Statements

Don't test if the statement is `false`. That becomes confusing fast.

  ```javascript
  // Bad
  var value = !condition ? false : true;

  // Good
  var value = condition ? true : false;
  ```

No more than a single condition should go into a ternary statement. Use a switch-case or if-else condition instead.

## Unused Variables

If a variable is not used, remove it.

## `var` Declarations

It is preferred to group all `var` declarations together to save bytes over-the-wire.

```javascript
var i, max, time, fmt,
    d = document,
    f = d.createDocumentFragment();
```

## Variable Definitions

The use of a variable before it was defined is prohibited.

JavaScript has function scope only and, in addition to that, all variables are always moved -- or hoisted -- to the top of the function. This behavior can lead to some very nasty bugs and that's why it is safer to always use variable only after they have been explicitly defined.

For more in-depth understanding of scoping and hoisting in JavaScript, read [JavaScript Scoping and Hoisting](http://www.adequatelygood.com/2010/2/JavaScript-Scoping-and-Hoisting) by Ben Cherry.

Also, the use of explicitly undeclared variables is prohibited. Most cases of this are typically typos.

```javascript
function test() {
    var myVar = 'Hello, World';
    console.log(myvar); // Typo
}
```

Lastly, use `||` notation to simplify setting a default value for an optional parameter/variable.

```javascript
function test(step) {
    step = step || 1;
}

test();  // `step` is 1.
test(5); // `step` is 5.
```

## Variable Placement

In conditions, the value should be on the left and the variable should be on the right. ([Supporting evidence](https://www.securecoding.cert.org/confluence/display/seccode/EXP21-C.+Place+constants+on+the+left+of+equality+comparisons))

  ```javascript
  var abc;

  // Encouraged
  if ("abc" === abc) {}

  // Discouraged
  if (abc === "abc") {}
  ```

## Variable Scope

Declaring variables inside of control structures while accessing them later from the outside is prohibited.

Even though JavaScript has only two real scopes -- global and function -- such practice leads to confusion among people new to the language and hard-to-debug bugs.

```javascript
function test() {
    if (true) {
        var x = 0;
    }

    x += 1; // 'x' used out of scope.
}
```

## Visibility

JavaScript doesn't have _real_ `public` or `private` members, but they can be emulated with scoping and closures.

```javascript
;(function() {
    var privateMethod = function() {};

    return {
        this.publicMethod = function() {};
    };
})();
```

## `==` or `===`

The use of `==` and `!=` are prohibited in favor of `===` and `!==`. The former try to coerce values before comparing them which can lead to some unexpected results. The latter don't do any coercion so they are generally safer.

If you would like to learn more about type coercion in JavaScript, we recommend [Truth, Equality and JavaScript](http://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript/) by Angus Croll.
