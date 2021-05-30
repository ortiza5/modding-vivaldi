# Sharing your Mods
Author(s): code3z (@code3 on the forum)

Once you've created a mod that you're proud of, the next step is to share it. Sharing will be a big help to other people. You can also get feedback and help from the community. But it may also mean you have to respond to bugs in your code and help other people use your code.

## Managing Mods

To share mods you need to be able to manage them well. The developer tool called Git can help a lot with this, and will also help others contribute and make your mods better. There are also some other recommended methods and formats that can help you organize your mods, please see the "Managing Mods" section of this guide.

## Code headers

Putting a comment at the top of your code helps people understand it, use it, and remember where it came from. Consider using this template:
```
/**
 * <TITLE>
 * https://forum.vivaldi.net/topic/<topic>
	- - -   
 * Description:        <description>
 <If your description is long, put the second part here>
 * Filename:          <filename>
 * Platform:          <Linux/Mac/Windows/All>
 * Version:           Vivaldi version <version>
 * Author(s):          <Here you can add your forum username, and your username for github or any relevant app (also add any other contributors here)>
**/
```

### Versioning Your Mods

Instead of tracking each edit to your mod as a separate version, its easier and sometimes more helpful to include the latest version of Vivaldi that it was tested in. Along with the last update time, this will let you and others know how up-to-date the mod is.

Because the forum and Git keep track of posting times, it's not necessary to include the last update time in the code header (but you can if you want).

If you do want to version your mods, it would look like this:
```
 * Version: 2.1 for Vivaldi 3.9.2289.3
```

If you want to keep it simple and use the last vivaldi version, it would look like this (see the header template above):
```
 * Version:           Vivaldi version 3.9.2289.3
```

## Tagging Forum Posts

Tagging your mods helps others find them. Use the forum tagging feature to insert the following tags, in addition to any others that make sense:
 1. [Mod]
 2. [CSS] and/or [JS]
 3. [Area] (what area of the UI does it affect?)

> Please don't make new tags on your own!

## Describing your mods

Now that you've added your code, titled your post, and tagged it, you need to write content! What you write is really up to you, but be sure to include what the mod does, how it will help people, and if it has any shortcomings or bugs or does not work with certain settings.

You should also include a screenshot. If the mod does something that can only be shown through a screen recording, take a screen recording and upload it as a GIF. You can find some screen recording tools in the resources section of this guide.

## Editing Posts
