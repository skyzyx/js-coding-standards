# Comments

* Non-documentation comments are strongly encouraged. A general rule of thumb is that if you look at a section of code and think "Wow, I don't want to try and describe that", you need to comment it before you forget how it works.

* C-style comments (`/* */`) and standard C++ comments (`//`) are both fine.

* For readability, add a single space after `//` style comments, and an extra space immediately inside both ends of a `/* */`-style comment.

  ```javascript
  // Encouraged Comment
  /* Encouraged Comment */

  //Discouraged Comment
  /*Discouraged Comment*/
  ```

* If you are making a longer, multi-line comment, use line breaks instead of spaces immediately inside both ends of a `/* */`-style comment. The content may, at your option, be indented as well.

  ```javascript
  /*
      This is an extra long comment that I'm breaking up
      into multiple lines for improved readability.
  */
  ```

* There should always be one line of whitespace above the start of a comment block.

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
