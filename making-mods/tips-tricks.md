# Tips and tricks

Author(s): tiosgz (potmeklecbohdan)

These are tiny tips and tricks that didn’t make it to a separate file.

## Contents

- [JavaScript](#javascript)
  - [Enclose your code in a function](#enclose-your-code-in-a-function)
  - [Inject CSS from JavaScript](#inject-css-from-javascript)

## JavaScript

### Enclose your code in a function

To prevent name conflicts with Vivaldi code and other mods, you may want to use
an IIFE (immediately invoked function expression).

```javascript
(function() {
  // Your code goes here
})();
```

### Inject CSS from JavaScript

If you have a mod in both CSS and JS and are absolutely sure that nobody will
customize the CSS and you won’t have to touch it until a major rewrite of the
mod, you can add the styles from JS to have everything in one file. But think
twice, because it will make both parts (less or more) harder to understand.

```javascript
// Just in case, check it isn't there yet
if (!document.head.querySelector('style#myModStyle')) { // Replace myModStyle
  const style = document.createElement('style');
  style.id = 'myModStyle'; // Again, replace myModStyle accordingly
  style.innerHTML = `
    * {
      background-color: red !important;
    }
  `;
  document.head.append(style);
}
```
