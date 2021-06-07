# Creating Your First Mod in CSS

In the previous guides you learned how to install mods, as well as how to open and use the built-in DevTools for CSS. In this tutorial you'll learn how to make a new mod using CSS.

Note that this tutorial assumes you have decent knowledge of CSS, please see "Resources" if you need to learn CSS.

> For this guide, turn the "floating panel" setting off  if you turned it on.

We'll try to solve the problem that Vivaldi's panels cannot be condensed past a certain limit.

To start, open up devtools using your preferred method and open a panel. Using the element selector, select the panel.

!()[]

Notice the element tree:

```HTML
<div id="panels-container" class="right" style="width: 260px">
  <div id="panels">
    <div id="switch">
      <div class="panel-group">
        <div class="panel-collapse-guard">
          <div class="panel panel-bookmarks">
            <div class="webpanel-stack hidden">
  <button type="button" tabindex="-1" class="SlideBar SlideBar--FullHeight alternate" style="">

```
Which one controls the width of the active panel?

Clicking on each of them, and using the devtools "filter" option to search for `width`, shows that `div.panel` has a `width` of `100%`, which just means its width is controlled by the parent element.

Its parent element, `div.panel-collapse-guard`, does have `min-width` and `max-width` defined. However, lowering these values (to, something like `100px`) just makes the panel look squashed, it doesn't decrease the space that the panel takes up.

![Squashed Panel Image](../assets/css-tutorial/squashed-panel.png)

You should be able to press `Ctrl + Z` to undo the changes. The next element up that has a defined width is `div#panels`, but that is also set to `100%`. The next element up, and seemingly the only panel-related element left, is `div#panels-container`. Adjusting it does change the width of the panel and makes the panel take up less space, but it hides some important panel content.

![Covered Panel Image](../assets/css-tutorial/covered-panel.png)

Correctly forcing a panel width will require changing both values: the width of the panel container and the width of the panel itself. Can you figure it out on your own? View the solution [here.](css-first-mod-part-2.md)

> Tip: Changing element.style will make your changes harder to export. Instead, use the "+" button in the styles tab to create a custom selector and style. Here is an example of what not to do:
  - 
> ![Do not edit style attributes](../assets/devtools/edit-element.style.png)

The main challenge with modding Vivaldi is that we didn't build the rest of the app and we can't ask the people who did, so there is a lot of inspecting we need to do. Sometimes you might need to inspect an element that autohides, or use CSS selectors on an element that has no class or ID. You can see the Tips & Tricks section of the guide to learn how to do things like that.
