## Upcoming Release

edbee.lib:

- fix #94 (partial), Resource delete fix in TextDocumentscopes
- Merged PR #86, Updated QsLog
- fix #89, Replace qSort with std::sort
- fix #84, Customize the autoScrollMargin
- Moved the TextLineDataManager to the core TextDocument
- Improves #82, Ctrl+Drag mouse while expands the last caret (allows multiple caret selections with mouse).
- fix #79, Using backtab on empty document causes Q_ASSERT failure
- ref #66, Automatic grouping of Changes that happen in repond of another event. (Crash in setText())
- add #60, Basic support for auto complete.
- add #59, Shift+Delete should perform a cut
- add #56, Added move line up/down commands.
- fix #58, Edbee crashes on Ctrl+Shift+Enter
- Made ChangeGroup non-virtual. Sometimes you need a group of undo-changes in stead of a mergable one (issues with move-line command)
- fix, Bug in Onig RegExp.cpp caused Ctrl+D to execute a regexp instead of a fixed string.
- fix #54, Use of raw string literal causes issues when QT_NO_CAST_FROM_ASCII defined
- fix #44, Commenting shortcut does not work if cursor is on the last character of the last line in the document
- add #45, Added ctrl-insert and shift-insert for copy paste
- fix #43, Added loadWithoutOpening and saveWithoutOpening to TextDocumentSerializer. For serializing without opening and closing an QIODevice (To enable the usage of QSaveFile).
- fix #41, Added LUA comments to the hardcoded list of comments
- fix #39, Margin-component bugfixes/improvements
	- Clicking/dragging changed so it behaves as expected. (Especially dragging up)
	- Line numbers of lines with selection are rendered with 100% opacity
- fix #38, Margin line-number font size is now set to the font size of the editor. It also renders number with an opacity of 0.5.
- fix #32, Changing showWhiteSpace option does not trigger a redraw
- add #31, Support for rendering borderedTextRanges. These are textranges rendered with borders, that aren't selected. TextEditorController has a member 'borderedTextRanges()'. Altering this rangeset (and updating the view controller::update) renderes borders aroudn the given ranges
- fix #30, Edbee crashes when you cut/copy with nothing selected. (Bug in clipboard operation)
- fix #27, Theme loading/handling bugfixes
	- Theme-colors with alpha channels are parsed correctly. (QColor expects #AARRGGBB, theme uses #RRGGBBAA)
	- Transparent main background color is changed to opaque to fix rendering issues.
	- Bugfixes TextThemeManager::theme, local scope shadowed returned theme value and double insert.
	- Setting the theme in Textrender now invalidates some caches
- fix #26, Changing a theme in the ThemeManager, now updates the ThemePointer used by the renderer. (Fixes corruption on theme reloading)
- fix #25, Removed the 'memory ok :-D' message
- fix #24, Clearing the undostack unregistered all controllers incorrectly
- fix #23, Scope invaldating optimization wasn't working correctly. Removed optimization for now
- fix #19, Workaround-hack for non-bmp-unicode character movement. (experimental)
- Added DebugCommand::DumpCharacterCodes (for dumping hex-character codes)
- fix #14, MinGW compatibility: Disabled memoryLeak detection and fixed mingw compilation (different library-name is generated for mingw)
- fix #13, Added a method to disable the scrollarea shadows: widget->textScrollArea()->enableShadowWidget(bool)
- fix #9, Updated onigmo library. Fixes compilation/linkage issue on Mac OS X (enc/windows_31j.c)
- fix, Fixed build warnings via een #pragma for the onig library. (When updating vendor/onig, include "config-onig-edbee.h" in "config.h")
- fix #5, Incorrect memory access after coalescing in TextDocument::ReplaceRangeSet. (Crash on Linux/Windows)
	This fix, changed the API interfaces of: (return type is now: Change*)
    - TextDocument::executeAndGiveChange
	- TextDocument::giveChangeWithoutFilter
	- CharTextDocument::giveChangeWithoutFilter
	- TextUndoStack::giveChange
- fix #4, QT5.8 Ambiguity Errors.
- fix #6, Theme Manager only attempts to load a theme if a theme path has been set.
- fix, updated Onigmo (Oniguruma-mod) library to version 6.1.1 (Fixes memory corruption with lexing)
- fix, removed config.h reference from simpleprofiler.h (Which caused compilation via to fail, refs issue #1)
- fix, mouse double click didn't select wordt anymore. (Issue with newer Qt version??)
- fix, moveCaret after the last character didn't work correctly on the if the last line didn't end with a newline
- fix, Syntax highlighting didn't work on the last line of the document. (First highlight after the first enter)
- fix, onig.pri, it contained strange references to qslog
- fix, edbee-lib.pri (correct references to vendor .pri's)
- BREAKING CHANGE, moved all source/headers files under the folder 'edbee/' to prevent filename collisions when embedding it in other projects.

Issues numbers below are issues from the old tracker.
All lines above refer to github-issue numbers

- add #121, Insert line before and insert line after commands
- add #108, #111, Added a DynamicTextRangeSet, a change aware rangeset, that automatically gets adjusted when the document changes.
- add #107, Implemented scoped/unscoped environment variable support
- add #33, Toggle comment line and comment block support using the TM_COMMENT_* environment variable structure.
- add #41, Duplicate Line support (Cmd+Shift+D)
- add #96, Multiple Cut line operations should append the lines together and grow the clipboard
- add #95, Command Delete should delete everything to the end of the current line
- add #93, Control Delete should delete the current 'word'
- add #94, Command Backspace should delete everything to the start of the current line
- add #91, Control Backspace should delete the current word
- add #85, Added scroll-past-end feature
- add #78, Added language independent smart tab support (enabled by default)
- add #79, Double clicking a selection with the control key again should remove the given selection and caret
- add #74, Added coalescing support for indenting / inserting tabs
- add #58, Pressing shift-delete now deletes the selected text
- add #43, Added right-click context-menu support to edbee. With default operations, cut, copy, paste and select all.
- add #36, Pressing shift-enter now inserts a newline
- add #31, Textsearching now also works with other ranges then textselection ranges
- fix, memory leak detection contained an incorrect iterator->second dereference. Causing crashes (Thanks Blackstar)
- fix #124, Line breaks (\n) are rendered with QTextLayout, which results in a strange character on a Linux environment (github issue 2)
- fix #123, Updated oniguruma to 5.13.5 to solve a segfault on Ubuntu 13 (64bits)
- fix #122, Library can't be compiled on Linux, unix  is a predefined word on unix
- fix #118, The width of the editor component should add an extra spacing so the caret isn't placed agains the right window border
- fix #117, The last line doesn't show the caret marker in the line-number column
- fix #116, The linenumber column isn't updated properly when the number of digets increases.
- fix #114, Added a factory keymap so the editor works out of the box
- fix #103, Renamed the *TextChange related classes. So it's more clear what the changes represent
- fix #73, Complete rewrite of coalescing (change-merging) algorithm, so all textchanges are mergable. (Fixes #98,#97,#95,#41,#99,#100,#101)
- fix #86, Pressing left or right when a selection is active shouldn't move the caret (current behavior is not-standard)
- fix #68, Adding a selection with Cmd+Mouse Double click shouldn't expand existing word selections
- fix #77, Pressing end of line on the last line, sometimes goes to the wrong location
- fix #76, Pressing enter doesn't scroll the horizontal window back to the first column
- fix #75, Goto pathname in treemenu doesn't display extension
- fix #72, TextDocument replaceRanges should calculate the ranges in stead of the TextChange event.
- fix #69, Plain Text was included twice by the grammar manager
- fix #57, Tab behaviour didn't work as expected when using space in stead of tab characters
- fix #48, Improved paste support with multiple lines, making it possible to copy/paste text per caret
- fix #61, Indent shouldn't indent the line after the text
- fix #66, Grammar type detection (by filename) detected the wrong grammars. (it forgot to check the '.' )
- fix #40, text now is by default case insensitive
- fix #30, #32, Searching selection via the findcommand now result in soft undoable changes
- fix #20, Changing TextEditorConfig now automaticly updates the state of edbee.
- fix #21, Improved fallback pallette when a theme cannot be loaded. (fixes complete black screen)
- fix #16, linespacing issue, the space always was at least 1 pixel
- fix #2, made it possible to configure TextEditorConfig. (was hardcoded)

## v0.1.0 Initial Release

The initial release on Github.
