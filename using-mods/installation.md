# Installation of mods

Author(s): tiosgz (potmeklecbohdan)

There are two ways to install modifications, each of them works for different
mods. While you can set up CSS mods once and then forget about them until they
break, you have to re-apply JavaScript mods each time you update Vivaldi.

## CSS

You will need to create a folder for your CSS mods somewhere (maybe in your
documents folder?). Make sure that the folder name and path to it **do not
contain a space**, otherwise the mods won’t work. Done?

Open Vivaldi and go to `vivaldi://experiments`, find the checkbox labeled
“Allow for using CSS modifications” and tick it. Open settings, go to the
“Appearance” tab, namely section “Custom UI modifications,” and select the
folder which you’ve created in previous step.

The steps until now have to be done only once. The steps below have to be done
for every CSS modification.

Create a plain text file in the folder that you’ve created in the first step.
It must be directly in the folder (**not in a subfolder**), or it won’t be
noticed by Vivaldi. Make sure that the file name contains **no spaces**. The
file name must also end with **`.css`** (you may have to enable something like
“show file name extensions” in the file manager).

Now open the newly created file with a text editor (for example Notepad), paste
the full code of the modification and save the file.

Restart Vivaldi. After that, you should see the effect of the modification. If
you do not, double check all the requirements above.

### Updating CSS modifications

When the author of a mod releases a new version, you will have to update your
local copy yourself. This is nothing hard: just find the file in which you saved
the original mod, open it, remove **all** text, copy-paste the new version into
it, and save it. When you are done updating, do not forget to restart Vivaldi.

### Disabling CSS modifications

To disable all CSS modifications at once, you can go to `vivaldi://experiments`
and untick “Allow for using CSS modifications,” or go to the “Appearance” tab in
the settings and clear the field under “Custom UI modifications.”

To disable only one modifications, you can rename its file so that its name
doesn’t end with `.css`. If you want to get rid of it completely, you can delete
the file.

Anyway, you will have to restart Vivaldi to see the changes.

## JavaScript

If you want to use JavaScript mods, prepare for more difficulties with their
installation.

There are various tools that do all the work for you (e.g. those in the pinned
topics on the [forum](https://forum.vivaldi.net/category/52/modifications) or
[LonM’s Python
script](https://github.com/LonMcGregor/VivaldiMods/blob/master/custom.py)). Each
of them is used differently and most of them have usage instructions included
somewhere. This guide describes how to install your modifications manually. If
you want to use [VivaldiHooks](https://github.com/justdanpo/VivaldiHooks),
follow the instructions at that repository.

It is recommended that you create a folder somewhere (in your documents folder?)
to store your JavaScript modifications. Vivaldi will not use this folder
directly, it is only for you to have everything in a safe place.

Place your JS mods into that folder. All of them are plain text files (if you
don’t know what that means, think Notepad) with `.js` at the end of their names
(you may have to enable something like “show file name extensions” to see this
ending).

Now you will have to find the folder where Vivaldi is installed. The usual
places are:

- on Windows: `resources\vivaldi` in a numbered folder in one of these:
  - `%localappdata%\Vivaldi\Application\` (you will have to paste it into the
    location field)
  - `C:\Program Files\Vivaldi\Application\`
- on Linux: `/opt/vivaldi/resources/vivaldi/` (or an `/opt/vivaldi-snapshot`
  variant)
- on MacOS: `/Applications/Vivaldi.app/Contents/Frameworks/Vivaldi
  Framework.framework/Versions/Current/Resources/vivaldi/` (or an
  `/Applications/Vivaldi Snapshot.app` variant)

Copy your JavaScript modifications into that folder. It is recommended to put
them in a new subfolder (called for example `mods`).

Just for case, back up `browser.html` found in the folder. Open the original
`browser.html` in a text editor. Find a line with `</body>`. For every JS mod,
insert a line like follows before the line with `</body>`:

```html
<script src="mods/custom.js"></script>
```

Do not forget to use the path to the actual file instead of `mods/custom.js`.
For example, if you have put it in the `mods` folder and it is called
`someCoolMod.js`, use `mods/someCoolMod.js`.

When you are done, save the file. After restarting Vivaldi you should see the
effect of the modifications.

### After a Vivaldi update

Every Vivaldi update causes all your JS mods to be removed. Follow the steps
above beginning with finding the folder where Vivaldi is installed (if you are
on Linux, you can usually skip the copying of modification files).

### Updating JavaScript modifications

To update a JS mod, edit the file in which it is stored: remove all text,
copy-paste all text of the new version and save the file.

Then you will have to copy the file into the folder within Vivaldi’s files (see
above where it is located).

### Disabling JavaScript modifications

To disable a JS mod, remove its line in `browser.html` (see above where it is
located).

To disable all JS mods at once, you can move the backup of `browser.html` back
to `browser.html` (it isn’t a bad idea to move the modified `browser.html` to,
let’s say, `browser-modded.html` before).

To completely remove a JS mod, apart from doing the above, remove its file so
that you don’t reuse it the next time you re-apply your mods.

// single file vs each in its own file
// hooks?
// creating the files, text editors
// sample mod?
