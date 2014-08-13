# Naming

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

* Code should be componentized. For example, a single widget should be self-contained. There should not be multiple widgets per file.
