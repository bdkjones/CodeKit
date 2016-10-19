#Release Candidate 7 (19 October 2016)
---------------------------------------------------

### NEW:
-- A build option to automatically create a .gitignore file in the build folder. It's on by default. Idea courtesy of @guymeyer. 

-- The project inspector now has a build project button at the bottom.



### Changed:
-- The "process all items" build step now handles all items that are not processed in any OTHER step, not just any PREVIOUS step. This lets you add a step such that certain files are built last.



### Fixed:
-- An issue where the browser would hang for ~30 seconds when a project that uses an External Server received a 301-Redirect response from that server.

-- When using an external server, the browser-injection script is now only injected in content that has a closing HEAD or BODY tag. Previously, it was injected in all content that had content-type text/html. The latter approach is still used for projects that do NOT use an external server.

-- A crash that could occur if you supplied invalid RegEx for a Hook's pattern matching rule.

-- Issue where Markdown files failed to compile if their output directory did not exist.

-- One of the command icons was misaligned by 1 pixel. @guymeyer caught it.


### Component Updates:
-- ESLint 3.8.1
-- TypeScript 2.0.3
-- Autoprefixer 6.5.1
-- Babel 6.16.0
-- SVGO 0.7.1






#Release Candidate 6 (+5) (10 October 2016)
---------------------------------------------------

### RC6 Fixes:

-- RC5 was short-lived. I ran into two additional issues that I wanted to fix immediately:

-- An issue where empty folders and skipped folders weren't displayed in the files list in RC5.

-- An issue where, upon refreshing a project, a literal shit ton of compiling occurred because CodeKit was under the false impression that all the stuff in your project was just added during the refresh.


### Fixed:

-- A crash if you opened the CodeKit Frameworks section of Project Settings and then removed the current project before switching to another one.

-- A rare crash when adding a project with a report that said, "Controller content cannot be nil".

-- Issue where the app sometimes stopped seeing file-change events in a Project until you refreshed the project.

-- Issue where the "New X Project" menu commands would fail if you selected a folder that's already in CodeKit as a project.

-- A crash that occurred if scanning a malformed file with ESLint.

-- If you combined multiple project folders into one while CodeKit was NOT running, the app failed to detect that the projects were merged when it started up. That would have led to a world of pain. Projects you combine into others are now removed when the app restarts.


### Changed:

-- The .codekit-cache folder is no longer created unless it's actually needed.

-- Inspector strings are now title-cased to match macOS conventions.

-- The Google Web Starter Kit install process is now overhauled to work correctly with a build folder. It's actually really slick.

-- Susy updated to 2.2.12

-- To streamline handling for MASSIVE projects and massive simultaneous file-events (think dragging 400 subfolders around in a project), CodeKit will no longer automatically update the output path of a source file if you rename/move that source file's output file. This was a very subtle feature and it's not clear that it exists. Users may not even realize it has occurred. The simpler, cleaner rule is: "if you want to change a file's output path, you do it in CodeKit's UI."


### New:

-- If there is no selected project in CodeKit, your web browser will display a "no active project" page instead of a 404. Much clearer. Idea was Guy's.


### Plan:

-- I intend to do one more RC with TypeScript 2.0. Barring any major bugs, that will become the GM.



# Release Candidate 4 (4 October 2016)
---------------------------------------------------

### New--Locking Output Paths

-- You'll see a new padlock icon next to output paths in the inspector. This functionality has always been part of CodeKit since version 1.x, but it's never been user-exposed before. When you set an output path manually using the "change" button, CodeKit marks that path as "locked", meaning the app won't automatically change it anymore. Normally, if you have not manually set an output path, the app will adjust the output path as the source file moves/renames. The lock button allows you to (1) see this state for the path and (2) change it. 

### Kit Improvements:

-- Kit files now respect indentation when importing files. The contents of an imported file will be indented by the same amount of leading whitespace there was before the special import comment.

-- Variable declaration comments in Kit will no longer produce blank lines in the output file, so long as there is no trailing whitespace after the end of the special comment that declares the variable.


### CSS Improvements:

-- Can now set the OutputStyle for regular CSS files. Same as Sass.

-- Source maps now available when processing regular CSS files.


### Hooks:

-- Hooks now inherit the ENV that CodeKit itself runs in. Fixes issue where PATH wasn't set correctly, so you couldn't call stuff without doing /usr/bin/...

-- When Hooks run successfully, their output is now logged correctly in CodeKit's log.

-- Hooks now run with /bin/bash instead of /bin/sh


### Fixed:

-- An issue where builds failed if "clean build" was enabled and the build folder did not exist when the build started.

-- Issue where the "don't show this for 1 hour" link on the "laggy connection" banner did not work.

-- MultiMarkdown updated to 5.4. Fixes several issues with MD files.

-- The folder icon was backwards on the window overlay that appears when you add a project.

-- An issue where running AutoPrefixer or Bless on a regular CSS file would overwrite the source file.








# Release Candidate 3 (27 September 2016)
---------------------------------------------------

### NEW: Kit Optionals

-- The Kit language now has "optionals". They look like this: &lt;!-- $myVar? --&gt;

-- The trailing question mark means, "If $myVar has a value, put it here. Otherwise, do nothing."

-- Kit variable names may no longer end in a '?'. This will produce an error: &lt;!-- $myVar? = something --&gt;

-- This makes it very easy to do active classes on items in a Nav menu. You know, if someone were building a website and needed such a thing. It would be handy if that person could just change an entire language to make the task simple.


### Changed:

-- When CodeKit creates import links for JS and Coffee files, it will now check to see if the imported file's path contains "node_modules" or the path to your "bower_components" folder. If it does, syntax-checking is automatically turned off for that imported file. No more "jQuery has 1,441 errors".

-- CodeKit is now pulling resources from the new URL: codekitapp.com. Many of the help links are 404-ed at this point, but will work once the new site goes live. You should find that the Bower components list download is much snappier. 

-- WARNING: The updater may tell you that a new version of CodeKit is available. It is not. Do NOT attempt to update the app. Just click "Skip This Version" in the window. This is just me testing the updater on the new URL.





# Release Candidate 2 (20 September 2016)
---------------------------------------------------

### New:

-- SourceType and ECMAVersion options now available for ESLint. Right at the top of Project Settings.

-- Additional operators (including full Regex matching) for Hook conditions

-- There's now a deprecation alert if you choose "New Compass Project". Turns out Compass is no longer under active development.

-- The default Skipped Items list now includes a path to skip logs for a default laravel install. This won't affect you guys, since your defaults are already set, but it will apply to users who upgrade to 3 upon release.


### Fixed:

-- Issue where the files list scrollView cut off prematurely after dragging a JS file to the Linked Files tab.






# Release Candidate 1 / Beta 16 (18 September 2016)
---------------------------------------------------

### New:

-- (Be sure to read all the Beta 15 stuff; LOTS of big new things)

-- CodeKit now passes plugins AND presets to Babel if you enable any of them. The order it passes presets has been set from "most experimental" to "least experimental". If you use the decorators plugin, CodeKit also makes sure it comes before the classes one. (This is obviously not done if you set these in a .babelrc file---see below.)

-- The "transform-decorators-legacy" Babel plugin is now built-in

-- You can now set CodeKit to ignore/merge/use-exclusively .babelrc files. If you need to fine-tune babel's configuration, choose "use .babelrc file settings only" and CodeKit won't pass any options to babel other than the one that creates an output file at the specified location for your input file.


### Changed:

-- ESLint updated to 3.5.0. New rules.

-- Babel now at 6.15.0

-- New icons for ESLint and Babel. 

-- The Components tab of the About window now has a nice fading top border. Details matter.








# Beta 15 (16 September 2016)
-----------------------------

### New:

-- "AutoBuild": Your project uses a build folder. The document root for the preview server is the build folder. You add an image. But to have it show up in the preview, you have to build the project so that CodeKit processes that new image to the right spot in the build folder. This now happens automatically. Add the image, the project will refresh, after the refresh completes any new or renamed items are processed. (This only happens if you use a build folder.) It can be toggled in Project Settings > Build Process. REALLY need to test this feature to make sure it's working well.

-- "Clean Builds": Before building, CodeKit will delete all existing items in the build folder. Again, this can be toggled in Project Settings > Build Process.

-- Many new project icons

-- Kit files can now use root-relative import statements: @import "/somefolder/somefile". These are always resolved from the project root folder.

-- A new command in the Tasks menu: "Apply Best Defaults For Using Build Folders" will automatically adjust the New Project Defaults for every language so that output paths and actions are set up for build folders automatically. Handy. I see myself writing many emails telling people to use this.


### Fixed:

-- An issue where the app would not process file-change events that occurred during a Project Refresh. Those changes are now queued for when the refresh completes and are then fired correctly.

-- An issue where ESLint failed to run because my NPM-Cleaning script deleted a needed file

-- When editing New Project Defaults, the app icon is now displayed in the General tab.






# Beta 14 (13 September 2016)
--------------------------

### NEW:

-- You can now add arbitrary file extensions as "other" languages in both Project Settings and New Project Defaults. This lets you specify custom output-file-path rules for these languages. Please test this extensively; it may be fragile.

-- CodeKit will now refresh "partial" pages. That is, your page need no longer have a HEAD tag. It simply needs to have the text/html content-type header. If your page DOES have a head tag, CodeKit will put its script there. Otherwise, it looks for a body tag and puts it there. Failing that, it just throws the script at the end, which lets you refresh pages that aren't even valid HTML.

-- PNG, GIF and JPG are now listed as languages in Project Settings


### Fixed:

-- An issue that would cause changes to file-output-path rules in the "New Project Defaults" area to not apply correctly. 

-- The Command Column buttons (left-hand side) now have a pressed state

-- Issue where two projects could point to the same folder if you follow a very specific set of steps with one project disabled. This caused chaos.

-- Build Settings are now read-only once the 3.0 trial has expired

-- Hitting the back button in your browser while viewing the Preview URL will no longer produce the dreaded "connection to CodeKit lost" red banner. The page stays connected.

-- Issue where the "Apply Default Output Paths to Existing Files" did not work in Project Settings.

-- That "apply to existing files" button is now disabled when in New Project Defaults mode


### Changed:

-- ES2015 and ES2016 are now the default Babel Presets. This will affect new users, but won't modify the New Project Defaults for existing beta testers.

-- Uglify.js updated to 2.7.3

-- SVGO update to 0.7.0. Includes "removeXNLNS" rule

-- AutoPrefixer 6.4.1





# Beta 13 (26 August 2016)
--------------------------

### NEW:

-- Hooks have changed. Until now, Hooks have been run at the END of a group of files being processed. (Like if you saved 4 files at once, your Hook ran once after all 4 files had been processed by CodeKit's built-in steps.) From now on, Hooks run once FOR EACH FILE. You'll find the same CK_INPUT_PATHS and CK_OUTPUT_PATHS environment variables set for Bash scripts, but your Hook will run over and over for each file that it matches, AS THE FILE IS PROCESSED. CodeKit's built-in steps go first, then your Hook. This is easier for users to Grok and it makes Hooks a bit easier to write. You'll see your Hook results in the same result message as the rest of CodeKit's processing for a given file; there are no longer separate messages for Hooks. It's all just much cleaner and "what you expect".

-- You can now tell CodeKit to use .eslintrc files instead of (or in addition to) the UI settings.

-- The JPEG optimizer should be much faster. 

### Fixed:

-- A crash that occurred if you added a "run script" build step and built the project without first refreshing it once.

-- Builds now actually stop on the first error if set to do so. You may see an additional few files compile after the first error. That's because CodeKit is processing 8 files at once, so the others have to finish up before the build is canceled.

-- Image optimizers will no longer fail because the output folder doesn't exist.

-- An issue where the JS import linker falsely identified huge lines of a minified file as potential import statements

-- Browsers no longer refresh if all you're doing is checking the syntax of a file

-- Generic files now have a "Process" button in the inspector.

-- All compilers now set a NODE_PATH Env variable so that node modules installed in either the project's root folder or next to the file being compiled will be found. Example: ESLint plugins.

-- Issue where some folders were falsely reported as children of existing projects when you attempted to add them to the app





# Beta 12 (15 August 2016)
--------------------------

### NEW:

-- AppleScript API endpoint to build a project

### Fixed:

-- A crash that could happen during a build

-- An issue where saving any file that's not a stylesheet would not trigger a browser refresh

-- The "process remaining items" build step title is no longer editable

-- An issue where Hooks might be run twice for each build step during builds





# Beta 11 (10 August 2016)
--------------------------

### THE BUILD PROCESS:

-- The build process is complete and active. I made a short video about how it works, including a discussion of WHY it works the way it does. Watch the video, then give it a shot: https://www.dropbox.com/s/irq4z7w8wm9949h/The%20Build%20Process.mp4?dl=0


### Changes:

-- The project config file can now be hidden. The option is in the General tab of Project Settings.

-- Hooks set in "New Project Defaults" (if any) will now migrate from 2.x to 3.0. Not for you guys, because you've already installed 3.0 once, but for everyone else they should come across.







# Beta 10 (26 July 2016)
------------------------

### New:
The UI for the BUILD section is now complete. Please give it a go; I'm hoping it's self-explanatory. You can add steps to the build flow and those steps will be saved in your project config, but the actual "build project" button does not yet do anything. There's a couple things to finalize there; it will be active in the next beta. In the meantime, please take a look at the build UI and let me know what you think, etc.

### Changes:

-New file icons for all types that CodeKit supports (Less, Sass, etc.)

-The 'codekit3.config' file is now double-clickable to add or switch to a project in the app.


### Component Updates:

-pug 1.0.0-alpha6

-autoprefixer 6.3.7

-uglify-js 2.7.0

-stylus 0.54.5

-eslint 3.1.1 (bunch of new rules)

-babel 6.11.4

-less-clean-css 1.5.1

-node 6.3.1

-neat 1.8 (no longer requires Bourbon)





# Beta 9 (13 July 2016)
-----------------------

### Critical:
The name of the settings file has changed from "codekit3.config" to "config.codekit3". For projects that you've been using with the CodeKit 3 beta, you need to manually change the name of the config file before you add the project to Beta 9. Otherwise, the app won't use your saved settings for that project.


### Fixed:

-- The "Apply To Existing Files" button in the Languages section of Project Settings now works.

-- Continued Build implementation (it's coming; I swear.)

-- Other stuff I forgot to put in my Git notes.






# Beta 8 (29 June 2016)
-----------------------

This release fixes a few things. I've mainly been working on the build flow, which has had to change pretty dramatically after I realized there was a shortcoming in my earlier approach. While it looks like this release doesn't have too much in it, there's a LOT going on under the hood to make the build process come together. Hang in there.

### Fixed:

-- Renaming files will now (again) correctly trigger a project refresh to capture the change.

-- The item counts in the project sidebar and popover now stay in sync.

-- The project sidebar's subtitles are no longer editable.

-- If you rename a project folder on disk, CodeKit now adopts that new name in the UI unless you have previously edited the name in the UI to assign a specific value.

-- The rare and incorrect "missing on disk" for newly-added projects should FINALLY no longer occur. 

-- Dragging to reorder Hooks would sometimes drop the dragged Hook in the wrong spot due to a bug in NSTableView. That has been worked-around.



# Beta 7 (15 June 2016)
-----------------------

### CRITICAL: 
Beta 7 includes a new config file format. If you are not careful, it will obliterate your settings and output paths for existing 3.0 projects created with Betas 1-6. To avoid that, do the following:

1. Download the "CK3Migrator" zip from this repo.
2. Open a Terminal window and use the cd command to switch to a directory that contains "codekit3.config" files generated by betas 1-6.
3. Drag and drop the unzipped CK3Migrator onto the Terminal Window.
4. Hit Enter. 

This tool will recursively walk every subfolder from the one you CD-ed into and look for files named "codekit3.config". When it finds one, it rewrites that file in the new format for Beta 7+. You can run it on your /Users/[myusername] folder to make sure you cover everything. This is only needed for 3.0 projects that have been in Betas 1 through 6. Projects that you have not yet added to CK3 (but which contain a CK2 config file) will automatically adopt the new Beta7+ format.

For a project with 30,000 files, this new format creates a 6.8 MB config file versus an 11.9 MB file under the old 2.x format.


### Fixed:
-- A crash that could happen in the Project Settings migrator

-- A crash that could happen when loading various popovers in the app

-- The "Skip This Folder" contexual menu item is now greyed out when used on an already-skipped folder

-- The red "disconnected" banner should no longer flash as you navigate pages in the preview server.

-- The build folder is now skipped only if your project is set to use a build folder. Otherwise, it's indexed normally.

-- An issue where creator/created files might not have been linked correctly

-- An issue where selecting files in the list and right-clicking to choose "Set New Output Path" screwed up the output filename of every file but the first.


### Changed:

-- All references to "OS X" are now "macOS". It's a brave new world.






# Beta 6 (12 June 2016)
-----------------------

### Critical Warning:
I'm going to change the format of the config3.codekit file to make it smaller for really large projects. To ensure you don't lose your settings, you need to download this beta release and add to the app every project you want to keep your 3.0 settings for. Then, install the next Beta when I release it. That one will not reset the data in the app, but it will write the new settings file format. As long as your projects are in Beta 6 when you install Beta 7, you'll be fine. 


### New:
-- The Browsers pane in Preferences has a new option to choose the default Preview Address.


### Changed:
-- Skipped Folders are now displayed in the UI with a custom inspector. If your project uses a build folder, you can choose to copy those folders to the build folder when the project builds.

-- The Build folder is now always skipped, if the project uses a build folder.

-- The project settings file for larger projects is much smaller. 30,000 file project was 11.9MB and is now 8.5MB. The next release will improve this even more, but I had to ship this one first to preserve your settings.


### Fixed:
-- Text is no longer blurry on non-retina screens.

-- PNG and JPEG optimizers now copy files to output paths correctly

-- A potential crash in the preview server if your project uses an external server

-- The Project Settings icon is fixed for non-retina

-- TypeScript files now minify output, if that's selected

-- An issue where settings could be lost for certain files if you moved them around on disk in a certain way

-- An issue where the app would falsely report one project was a child of another if the names were similar. e.g. "myProject" and "myProject-other"

-- An issue where the "Skip This Item" contextual menu command did not work on the clicked row.

-- Skipped Items list in project settings no longer cuts off text

-- An issue where build folder output paths could be calculated incorrectly for certain source folder paths

-- The "Change" link for setting a new Output Path is now hidden if the file is set to "ignore".

-- An issue where saving files in Coda 2 would trigger a project refresh instead of a processing action.






# Beta 5 (31 May 2016)
----------------------

### New:
-- Cmd+F will now bring up the search field if you're in a part of the app that can be searched.

-- JavaScript files now support ES6 'import' syntax. CodeKit will correctly map dependencies between files that use 'import'. A third section appears in the "Linked Files" pane of the JS inspector that shows these imports. The old @codekit-prepend/append statements are still supported, but you should not use both at once. Currently, CodeKit doesn't *do* anything with these links; you'll have to enable Babel and use the commonjs module to transpile the files into a single JS file that can be used in current browsers.


### Fixed:
-- An issue where the search fields would de-select themselves

-- An issue where Sass partials were not linked correctly by the import scanner

-- An issue where the TypeScript compiler's error messages weren't shown in the log.

-- An issue where the TypeScript compiler would report insanely long, relative file paths in error messages.

-- An issue that caused certain TypeScript import statements to not be detected correctly by the import linker






# Beta 4 (28 May 2016)
----------------------

### New:
-- TypeScript files using "import" statements now link dependent files correctly so CodeKit can compile the right parent file when dependents change. (The older "reference path" style is also still supported.)

-- ALL of CodeKit's import scanners have been refactored in this release. (This is groundwork to support ES6 imports in JavaScript and prepending/appending skipped files.) As a result, I need to test EVERY language in the app to make sure imports are still found correctly---especially imports that target CodeKit Frameworks.


### Changed:
-- New Preview icon.

-- Server icon has a chevron to more clearly indicate what it does.

-- Log messages are now monospaced

-- Log coloring tweaked


### Fixed:
-- "Use Libsass" checkbox is now disabled in Compass projects

-- If you change a setting and quit the app immediately afterwards, that change is now recorded in the project's config file before the app quits.

-- Changing Build Folder settings now resets the Preview Server correctly.

-- An issue where the app would incorrectly report that Project B was a subfolder of Project A when you attempted to add B to the app.

-- Stylus files now compile. 

-- Jade AND Pug files should now compile correctly.

-- An existing project can now never be added twice, even if CodeKit's file-watching is paused and you rename the project
 



# Beta 2 (23 May 2016)
----------------------

### New:
-- Hooks now add messages to the Log when they exit with a (0) code and print anything to StdOut or when they print anything to StdErr, regardless of exit code.

-- You can now add a Log message via AppleScript. See the AppleScript dictionary for the API.

-- There are additional commands in the Status Bar menu so you can control the app when running without the Dock icon.

-- JSX file extensions are now treated as JavaScript files.

-- The dock icon now switches to white when you enable Dark Menu mode.


### Fixed:
-- Issue where syntax errors were sometimes hidden in the log.

-- Issue where the "no projects" message might be truncated in the projects popover.

-- Issue where Jade files would compile but Pug files would not. 

-- Babel no longer writes a source map when maps are off.

-- The project title sometimes migrated down the window. It should not do that anymore.

-- It's no longer possible to change the output path of a Sass file in a Compass project. 

-- The "New Group" commands are now unavailable in the Projects Popover if there are no projects or frameworks in the app.

-- The default "Projects" and "Frameworks" groups can no longer be renamed.

-- Group names can now be edited by clicking anywhere. Previously, you had to click the first 30 pixels



### Changed:
-- Wider Preview icon with larger click target

-- ESLint updated to version 2.10.2. Couple new rules added.

-- ESLint has moved to the top of the Sytax Checkers list so that people use it.




# Beta 1 (17 May 2016)
----------------------

- Initial Release
- Forgot to mention in the video: If you add a Hook that runs on file types for which CodeKit does not have built-in processing (such as minifying HTML), those Hooks will be run as long as the file's output option is not 'ignore'.
- Gif optimization is also a thing. Select a Gif in the app to see it.
