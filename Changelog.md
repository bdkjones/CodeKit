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
