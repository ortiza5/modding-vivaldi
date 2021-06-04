# Inspecting the Vivaldi UI with DevTools

Author(s): luetage

Developer Tools allow us to inspect Vivaldi’s user interface and debug our
modifications. Loading devtools the usual way (keyboard shortcuts, inspect from
menu, &c.) won’t necessarily give us access to the interface, however. In the
following section we want to look at different ways how to achieve this.

---

## Loading DevTools

In the past we were able to add a command line flag to the executable, enabling
debugging. This extendend all right‐click menus in the UI and allowed us to
inspect specific elements directly. Chrome version 89 deprecated this option,
therefore we have to resort to alternative methods.

- Open **`vivaldi://inspect/#apps/`** and click “inspect” beneath the first line
  (Vivaldi browser.html).
- Open **`vivaldi://settings/`** in a **tab** and load devtools with a keyboard
  shortcut, quick commands, or menu entry (e.g. `Main Menu — Tools — Developer
  Tools`).
- Open **`vivaldi://experiments/`**, load devtools.
- Open **`vivaldi://mail/`**, load devtools.
- Enable “Show Introduction” for private windows in `vivaldi://settings/privacy/`.
  Open a **private window**, load devtools.
- Start Vivaldi with the command line flag **`--remote-debugging-port=9222`**.
  Open another browser (the stable/snapshot version of Vivaldi for instance) and
  visit **`http://localhost:9222/`**. Select the line containing `browser.html`
  to inspect the user interface.


Devtools will always load in a new window; we are not able to attach them to the
current window. Depending on your setup and preferences, you can create
bookmarks for these sites with optional nicknames, dedicated menu entries for
both the sites and the different developer tools commands (Element Inspector and
Console) and custom keyboard shortcuts. This assures devtools for the UI are
only ever a few clicks, or keystrokes, away.

---

## Using DevTools

A short introduction in 2 examples.

### Element Inspector

![Developer Tools][devtools screenshot]

The element inspector allows us to look up selectors for the elements we intend
to modify. Let’s change the font color of the active tab.

1. Open devtools and click the element picker button (mouse pointer) on top left.
   It turns blue.
2. Hover the active tab in the Vivaldi window and move around until you see the
   span element with the `.title` class.

    ![Inspect UI][inspect screenshot]

3. Click to select. The element is being highlighted in the “Elements” tab,
   which represents the page source of the user interface.
4. A second section inside the tab contains the “Styles” tab either at the
   side or beneath. In the source we can find the selectors, the style shows the
   CSS acting on the selected element. Scroll down until you find the command
   that changes the color of the active tab.

    ![Edit style][edit style screenshot]

5. Click on `var(--colorAccentFg)` (this is an example, the color could be
   different in your theme), press `backspace`, input `red` and press `enter`.
   This changes the font color, but only temporary (until reload).
6. Should you have the experiment for using CSS modifications enabled in
   `vivaldi://experiments/`, you can both access and edit your modification
   files in the developer tools. Click on the “Sources” tab and in the sidebar
   expand `vivaldi-data` and then `css-mods`. Click on your mod file, the
   contents will be shown right next to it. Since we know how Vivaldi changes
   the color of the active tab, we can use the same code in our file to
   overwrite Vivaldi’s instructions. Change the color to `green` this time and
   notice how the change is immediately visible.

    ![Edit file][edit file screenshot]

7. This is a temporary modification too. However, we can make our edit permanent
   by right‐clicking and selecting “Save as...”. Choose the location of the mod
   file to overwrite, or save the edit as backup.

---

### Reloading the user interface

The standard way of performing edits is opening our mod file in a proper text
editor, editing, saving and reloading the UI. Here a few options to load the
changes:

- Exit Vivaldi and open it again.
- Open a new browser window.
- Select all tabs and move them to a new window. This is available as a menu
  entry when right‐clicking a tab and has the advantage of keeping sites and
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

---

### Console

Let’s write a “Hello, World!” example script for testing our Javascript setup as
described in [Installation][installation link].

1. Open the javascript modification file in a text editor.
2. Copy and paste following code and save.

    ```Javascript
    setTimeout(wait => {
      const browser = document.getElementById("browser");
      if (browser) console.log("Hello, World!");
      else setTimeout(wait, 300);
    }, 300);
    ```

3. Reload the user interface and load developer tools.

    ![Hello, World!][hello world screenshot]

4. Click the “Console” tab, our message should be visible.
5. Now we introduce an error. Delete the first line of the script and reload UI.

    ![Error][error screenshot]

6. Open devtools and switch to the console. Vivaldi detects the error at line 8,
   where the closing bracket is located. We deleted the opening bracket, so this
   is expected. Console logs are one way to test the functionality of our mods
   and find errors—use them to your advantage.

---

I hope these instructions have been helpful. For further questions post a reply
to the [original topic][original topic link]; we have a healthy community
willing to help you out.

[devtools screenshot]: /assets/inspecting/devtools.png
[inspect screenshot]: /assets/inspecting/inspect.png
[edit style screenshot]: /assets/inspecting/edit-1.png
[edit file screenshot]: /assets/inspecting/edit-2.png
[installation link]: installation.md
[hello world screenshot]: /assets/inspecting/hello-world.png
[error screenshot]: /assets/inspecting/error.png
[original topic link]: https://forum.vivaldi.net/topic/16684/inspecting-the-vivaldi-ui-with-devtools
