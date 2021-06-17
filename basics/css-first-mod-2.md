# Continuing with our First CSS Mod

Here is the solution to the CSS mod:
```CSS
div#panels-container .panel-collapse-guard {
    max-width: 190px !important;
    min-width: 190px !important;
}

div#panels-container {
    width: 124px !important;
}
```

But, you may notice that

## Allowing for multiple setups

When modding it's important to think of different setups, such as having the
panel floating or having it inline (you can change this with a Ctrl-click on
the panel button in the status bar).

## Making the mod user-friendly

We can make the mod more user-friendly by allowing the user to disable the mod
when the panel is not at its smallest position, using some CSS tricks.

```css

:root {
    --panel-condensed: 190px

}
div#panels-container[style="width: 260px;"] .panel-collapse-guard {
    max-width: var(--panel-condensed) !important;
    min-width: var(--panel-condensed) !important;
}

div#panels-container[style="width: 260px;"] {
    width: calc( var(--panel-condensed) + 34px) !important;
}
```
