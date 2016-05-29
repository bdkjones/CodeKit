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
