# Grammar

* Global variables
    * No. ಠ_ಠ

* All code should be properly encapculated, and only expose the things that need to be available under a project namespace of some sort. (We don't want to pollute the global scope.)

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

* If your code is intended to support modern browsers, use `application/javascript`, as per [RFC-4329 §7](http://tools.ietf.org/html/rfc4329#section-7). If you need to support a version of Internet Explorer earlier than 9.0, you must instead use the obsoleted `text/javascript`.

  ```html
  <script type="application/javascript">
      // ...
  </script>
  ```

* All control structures use braces, even if they’re optional.

  ```javascript
  // Bad
  if (condition) $abc = 'abc';

  // Bad
  if (condition)
      $abc = 'abc';

  // Good
  if (condition) {
      $abc = 'abc';
  }
  ```

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://tools.ietf.org/html/rfc2119).

* Files MUST use only UTF-8 without BOM for JavaScript code.

* Code MUST use tabs for indenting, not 4 spaces.

* Control structure keywords MUST have one space after them; method and function calls MUST NOT.

  ```javascript
  if () {}
  else () {}
  function example() {}
  ```

* Opening parentheses for control structures MUST NOT have a space after them, and closing parentheses for control structures MUST NOT have a space before.

  ```javascript
  if ("abc" === abc) {}
  ```

* An empty line feed should precede a return statement.

* Remove trailing whitespace at the end of lines.

* A file must always end with an empty line feed.

## Arrays/Objects

* Short array/object syntax should be used.

  ```javascript
  // Bad
  var a = new Array();
  var b = new Object();

  // Good
  var a = [];
  var b = {};
  ```

* If any array elements have their own line, they all should. Avoid inconsistency where some are on the same line and others are not.

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

## Strings

* Double quotes most of the time, as they are required for [JSON](http://json.org).

## Ternary statements

* Don't test if the statement is `false`. That becomes confusing fast.

  ```javascript
  // Bad
  var value = !condition ? false : true;

  // Good
  var value = condition ? true : false;
  ```

* No more than a single condition should go into a ternary statement. Use a switch-case or if-else condition instead.

* In conditions, the value should be on the left and the variable should be on the right. ([Supporting evidence](https://www.securecoding.cert.org/confluence/display/seccode/EXP21-C.+Place+constants+on+the+left+of+equality+comparisons))

  ```javascript
  var abc;

  // Encouraged
  if ("abc" === abc) {}

  // Discouraged
  if (abc === "abc") {}
  ```

## `==` or `===`

* If you are comparing against an absolute value (e.g., a string, integer, boolean), always use `===`.

* If you are comparing against a _truthy_ or _falsey_ value, always use `==`.
