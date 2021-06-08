# Continuing with our First CSS Mod

Here is the solution to the CSS mod:
```CSS

```

Did you figure it all out? You likely figured out this part:

```CSS

```
If you did not, you may want to review CSS.


Maybe you also figured out this part, which allows the panel to be closed correctly:

```CSS

```
If you observe the changes of the panel in devtools, you can see that the
`icons` class is added to `div#panels-container` when the panel is closed (and
showing only the icons).

But let me explain this part:

``CSS


```
## Allowing for multiple setups

When modding it's important to think of different setups, such as having the 
panel floating or having it inline (you can change this with a Ctrl-click on
the panel button in the status bar).

## Making the mod user-friendly

We can make the mod more user-friendly by allowing the user to disable the mod
when the panel is not at its smallest position, using some CSS tricks.
