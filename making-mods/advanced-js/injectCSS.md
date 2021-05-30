# Injecting CSS with JavaScript

Author(s): code3z (code3 on the forum) and tiosgz (potmeklecbohdan on the forum)

CSS styles are fairly easy to add to Vivaldi, and most of the time you will probably use Vivaldi's native CSS mods manager. But for JS mods that require a little bit of CSS, you may want to combine the CSS in Javascript.

The benefit is that it's all in one file, and easier for users to install. The downsides are that the CSS is harder to customize, and the code is a bit harder to write.

<!-- tabs:start -->

#### ** **JavaScript Template** **

```JavaScript

(function () {
  let styles = document.createElement("style");
  styles.type = "text/css";
  styles.setAttribute("data-id", "<name-of-mod>-styles");
styles.innerHTML = `/* Add CSS styles here.
They can take up multiple lines. Example: */
* {
  color: #00ff00 !important;
}

`;
document.head.append(styles);
})();
```
#### **Example**

```JavaScript
(function () {
  let styles = document.createElement("style");
  styles.type = "text/css";
  styles.setAttribute("data-id", "history-clock-styles");
styles.innerHTML = `.panelbtn.history svg, .panelbtn.notes svg, .panelbtn.tabs svg {padding-top: 2px !important; width: 26px !important; height: auto !important;}
.panelbtn.history svg path {
  d: path("M 6 2 h 4 a 4 4 0 0 1 4 4 v 4 a 4 4 0 0 1 -4 4 H 6 a 4 4 0 0 1 -4 -4 V 6 a 4 4 0 0 1 4 -4 z M 1 6 a 5 5 0 0 1 5 -5 h 4 a 5 5 0 0 1 5 5 v 4 a 5 5 0 0 1 -5 5 H 6 a 5 5 0 0 1 -5 -5 V 6 z v 4 z");
  transform: translate(4px, 4px) scale(1.09);
  zoom: 1.1;
}
.panelbtn.history.active svg path {
  d: path("M 14 3 z M 1 6 a 5 5 0 0 1 5 -5 h 4 a 5 5 0 0 1 5 5 v 4 a 5 5 0 0 1 -5 5 H 6 a 5 5 0 0 1 -5 -5 V 6 z v 4 z")
}
.panelbtn.history.active svg rect {
  fill: var(--colorBg);
}
`;
document.head.append(styles);
})();
```
#### **Equivalent CSS**

```CSS
/* History Clock */
.panelbtn.history svg, .panelbtn.notes svg, .panelbtn.tabs svg {padding-top: 2px !important; width: 26px !important; height: auto !important;}
.panelbtn.history svg path {
  d: path("M 6 2 h 4 a 4 4 0 0 1 4 4 v 4 a 4 4 0 0 1 -4 4 H 6 a 4 4 0 0 1 -4 -4 V 6 a 4 4 0 0 1 4 -4 z M 1 6 a 5 5 0 0 1 5 -5 h 4 a 5 5 0 0 1 5 5 v 4 a 5 5 0 0 1 -5 5 H 6 a 5 5 0 0 1 -5 -5 V 6 z v 4 z");
  transform: translate(4px, 4px) scale(1.09);
  zoom: 1.1;
}
.panelbtn.history.active svg path {
  d: path("M 14 3 z M 1 6 a 5 5 0 0 1 5 -5 h 4 a 5 5 0 0 1 5 5 v 4 a 5 5 0 0 1 -5 5 H 6 a 5 5 0 0 1 -5 -5 V 6 z v 4 z")
}
.panelbtn.history.active svg rect {
  fill: var(--colorBg);
}
```
<!-- tabs:end -->

## More

You can probably just copy the code above, but if you want to know the reasons for it:

Multiline variables are possible due to [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals). If you use ${} anywhere in your CSS, you must escape by putting a backslash before it.

The code is wrapped in
`(function () {})();` because it [avoids having variables with the same name interfere with each other](https://developer.mozilla.org/en-US/docs/Glossary/IIFE#avoid_polluting_the_global_namespace

Because the ``<style>`` element was given a custom data-id, it can be selected like this:
```JavaScript
document.querySelector('style[data-id="history-clock-styles"]');
```

In order to be changed or deleted. The `data-id` is also useful when inspecting the code.
