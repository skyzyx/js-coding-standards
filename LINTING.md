# Linting

I use [JSHint](http://jshint.com/docs/) for linting my JavaScript code.

## Globals

Try to be as strict with yourself as possible by only adding your own namespace to the global scope. Even then, referring to it as `window.MyNamespace` is even better.

  ```javascript
  /* global MyNamespace */
  ```

## Error Reporting

I stick with the default value for displaying error messages.

  ```javascript
  /* jshint maxerr:50 */
  ```

## Enforcing Options

A value of `true` means that a stricter approach is applied. A value of `false` means that there is no enforcement. (These are line-wrapped for legibility.)

```javascript
/* jshint 
     bitwise: true,
     camelcase: true,
     curly: true,
     eqeqeq: true,
     forin: true,
     freeze: true,
     immed: true,
     indent: false,
     latedef: true,
     maxcomplexity: 10,
     maxdepth: 4,
     maxlen: 120,
     maxparams: 4,
     maxstatements: 10,
     newcap: true,
     noarg: true,
     noempty: true,
     nonbsp: false,
     nonew: true,
     plusplus: false,
     quotmark: true,
     regexp: true,
     undef: true,
     unused: true,
     strict: true,
     trailing: true
*/
```

## Relaxing Options

A value of `true` means that the linter supresses warnings about certain guidelines. A value of `false` means that the linter does NOT supress warnings about a guideline. (These are line-wrapped for legibility.)

  ```javascript
  /* jshint 
       asi: false,
       boss: true,
       debug: false,
       eqnull: false,
       esnext: false,
       esnext: false,
       evil: false,
       expr: false,
       funcscope: false,
       globalstrict: false,
       iterator: false,
       lastsemic: false,
       laxbreak: false,
       laxcomma: false,
       loopfunc: false,
       moz: false,
       multistr: false,
       notypeof: false,
       noyield: false,
       onecase: false,
       proto: false,
       regexdash: false,
       scripturl: false,
       shadow: false,
       smarttabs: true,
       sub: true,
       supernew: false,
       validthis: false
  */
  ```

## Environment Options

A value of `true` means that the linter will have environment-specific sets of rules to apply implicitly. A value of `false` means that the linter does NOT apply environment-specific sets of rules. (These are line-wrapped for legibility.)

  ```javascript
  /* jshint 
       browser: true,
       couch: false,
       devel: false,
       dojo: false,
       jquery: false,
       mootools: false,
       node: false,
       nonstandard: false,
       phantom: false,
       prototypejs: false,
       rhino: false,
       worker: true,
       wsh: false,
       yui: false
  */
  ```
