# [DRAFT] Continuing with our First CSS Mod

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

But, you may notice that the same value is repeated twice, and the second value
is just the first value + 34px (the width of `#panels-container #switch`, where
the panel buttons are). So we can use [CSS variables](#todo-mdn) like this:

```css

:root {
    --panel-condensed: 190px
}
div#panels-container .panel-collapse-guard {
    max-width: var(--panel-condensed) !important;
    min-width: var(--panel-condensed) !important;
}

div#panels-container {
    width: calc( var(--panel-condensed) + 34px) !important;
}
```

## Allowing for multiple setups

When modding it's important to think of different setups, such as having the
panel floating or having it inline (you can change this with a Ctrl-click on
the panel button in the status bar).

Make sure you test with open floating panel, closed floating panel, open inline
panel, closed inline panel, and right and left side panels.

## Making the mod user-friendly

We can make the mod more user-friendly by allowing the user to disable the mod
when the panel is not at its smallest position, using some CSS tricks.

Essentially, this allows the user to drag the panel to the smallest width
possible, and it will snap to an even smaller width. Remember, right-clicking
a panel button gives an option to make a certain panel a seperate width from
the others.

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
