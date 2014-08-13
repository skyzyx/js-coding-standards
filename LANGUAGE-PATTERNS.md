# Language Patterns and Best Practices

## Visibility

* JavaScript doesn't have _real_ `public` or `private` members, but they can be emulated with scoping and closures.

  ```javascript
  ;(function() {
      var privateMethod = function() {};

      return {
          this.publicMethod = function() {};
      };
  })();
  ```

## Assignments in Conditionals

* It can be very confusing for developers who think you have a typo (i.e. they assume you meant `==`, when you intentionally meant `=`).

* Because of this, doing variable assignments as part of conditionals is discouraged. Instead, try this approach:

  ```javascript
  var time = new Date();

  if (time > 0) {
      // code that uses time...
  }
  ```
