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
“Appearance” tab, namely section “Custom UI modifications”, and select the
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

## JavaScript

If you want to use JavaScript mods, prepare for more difficulties with their
installation.

// create a folder for mods

// create mods files

// find browser.html

// copy the files over

// edit browser.html





/opt/vivaldi[-snapshot]/resources/vivaldi/browser.html
/Applications/Vivaldi[ Snapshot].app/Contents/Frameworks/Vivaldi Framework.framework/Versions/Current/Resources/vivaldi/browser.html
%localappdata%\Vivaldi\Application\{version}\resources\vivaldi\browser.html
C:\Program Files[ (x86)]\Vivaldi\Application\{version}\resources\vivaldi\browser.html
