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
