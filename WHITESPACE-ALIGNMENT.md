# Whitespace and Alignment

* `switch` control statement:
    * The contents of each `case` or `default` block should be indented for readability. This includes the closing `break`.
    * There should always be a `default` block.

* Blocks of variable setting should have all `=` and `:` characters vertically-aligned.

* You are encouraged to give increment/decrement operators (`++` and `--`) a line of their own (with the exception of `for` loops).

  ```javascript
  foo[i++] = j; // Discouraged: relies on `i` being incremented after the expression is evaluated
  foo[--j] = i; // Discouraged: relies on `j` being decremented before the expression is evaluated

  foo[i] = j;
  i++;            // Encouraged: obvious when `i` is incremented

  j--;
  foo[j] = i;   // Encouraged: obvious when `j` is decremented
  ```
