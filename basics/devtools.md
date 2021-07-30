# Inspecting the Vivaldi UI with DevTools

Author(s): luetage

Developer Tools allow us to inspect Vivaldi’s user interface and debug our
modifications. Trying to access DevTools the usual way (keyboard shortcuts,
inspect from menu, etc.) won’t necessarily give us access to the interface,
however. In the following section we want to look at different ways how to
achieve this.

## Loading DevTools

Loading DevTools for the UI requires us to open one out of a set of specific
pages first.

- Open **`vivaldi://inspect/#apps/`** and click “inspect” beneath the first line
  (Vivaldi browser.html).
- Open **`vivaldi://settings/`** (in a **tab**), or **`vivaldi://experiments/`**,
  or **`vivaldi://mail/`** and load DevTools with a keyboard shortcut, Quick
  Commands, or menu entry (e.g. `Main Menu → Tools → Developer Tools`).
- Enable “Show Introduction” for private windows in `vivaldi://settings/privacy/`.
  Open a **private window**, load DevTools.
- Start Vivaldi with the command line flag **`--remote-debugging-port=9222`**.
  Open another browser (the stable/snapshot version of Vivaldi for instance) and
  visit **`http://localhost:9222/`**. Select the line containing `browser.html`
  to inspect the user interface.

DevTools will always load in a new window; we are not able to attach them to the current window. Depending on our setup and preferences, we can create bookmarks for these pages with optional nicknames, dedicated menu entries for both the pages and the different DevTools commands (Element Inspector and Console) and custom keyboard shortcuts. This assures DevTools for the UI are only ever a few clicks, or keystrokes, away. Alternatively we can create a command chain in `vivaldi://settings/qc`, which automates the process:

Command chain name: **Inspect UI**

1. Open Link in New Tab
    Parameter: `vivaldi://experiments`
2. Delay
    Parameter: `50`
3. Developer Tools
4. Close Tab

## Using DevTools

A short introduction in 2 examples.

### Element Inspector

![devtools image]

The element inspector allows us to look up selectors for the elements we intend
to modify. Let’s change the font color of the active tab.

1. Open DevTools and click the element picker button (mouse pointer) on top left.
   It turns blue.
2. Hover the active tab in the Vivaldi window and move around until you see the
   span element with the `.title` class.

   ![inspect image]

3. Click to select the tab title. The element is being highlighted in the
   “Elements” tab, which represents the page source of the user interface.
4. A second section inside the tab contains the “Styles” tab either at the side
   or beneath. In the source we can find the selectors, the style shows the CSS
   acting on the selected element. Scroll down until you find the command that
   changes the color of the active tab.

   ![edit style image]

5. Click on `var(--colorAccentFg)` (this is an example, the color could be
   different in your theme), press `backspace`, input `red` and press `enter`.
   This changes the font color, but only temporarily (until reload).
6. Should you have the experiment for using CSS modifications enabled in
   `vivaldi://experiments/` (see [Installation][installation link]), you can
   both access and edit your modification files in the DevTools. Click on
   the “Sources” tab and in the sidebar expand `vivaldi-data` and then `css-mods`.
   Click on your mod file, the contents will be shown right next to it. Since we
   know how Vivaldi changes the color of the active tab, we can use the same
   code in our file to overwrite Vivaldi’s instructions. Change the color to
   `green` this time and notice how the change is immediately visible.

   ![edit file image]

7. This is a temporary modification too. However, we can make our edit permanent
   by right‐clicking and selecting “Save as...”. Choose the location of the mod
   file to overwrite, or save the edit as backup.

### Reloading the user interface

The standard way of performing edits is opening our mod file in a proper text
editor, editing, saving and reloading the UI. Here a few options to load the
changes:

- Exit Vivaldi and open it again.
- Open a new browser window.
- Select all tabs and move them to a new window. This is available as a menu
  entry when right‐clicking a tab and has the advantage of keeping webpages and
  media playback active.
- Restart Vivaldi. The URL **`vivaldi://restart/`** will restart Vivaldi when it
  is being opened in the current tab. We can either enter the address directly
  in the address field, or use a bookmark. One nifty option is to save the
  address, assign a nickname to it (e.g. `re`) and load it with quick commands.
  `shift‐/alt-enter` will open in current tab, when bookmarks are set to open in
  a new tab by default and vice versa; this is dependent on our search,
  bookmarks and quick commands settings.

All the actions load the `browser.html` file anew, which in turn loads our
modification files.

### Console

Let’s write a “Hello, World!” example script for testing our Javascript setup as
described in [Installation][installation link].

1. Open the Javascript modification file in a text editor.
2. Copy and paste following code and save.

   ```javascript
   setTimeout(function wait() {
     const browser = document.getElementById("browser");
     if (browser) console.log("Hello, World!");
     else setTimeout(wait, 300);
   }, 300);
   ```

3. Reload the user interface and load DevTools.
4. Click the “Console” tab, our message should be visible.

   ![hello world image]

5. Now we introduce an error. Delete the first line of the script and reload UI.
6. Open DevTools and switch to the console. Vivaldi detects the error at line 4,
   where the closing bracket is located. We deleted the opening bracket, so this
   is expected. Console logs are one way to test the functionality of our mods
   and find errors—use them to your advantage.

   ![error image]

---

I hope these instructions have been helpful. For further questions post a reply
to the [original topic][topic link]; we have a healthy community willing to help
you out.

[devtools image]: /assets/basics/devtools/devtools.png
[edit file image]: /assets/basics/devtools/edit-file.png
[edit style image]: /assets/basics/devtools/edit-style.png
[error image]: /assets/basics/devtools/error.png
[hello world image]: /assets/basics/devtools/hello-world.png
[inspect image]: /assets/basics/devtools/inspect.png

[installation link]: installation.md
[topic link]: https://forum.vivaldi.net/topic/16684/inspecting-the-vivaldi-ui-with-devtools
