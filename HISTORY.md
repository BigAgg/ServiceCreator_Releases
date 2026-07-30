# v1.2.2 (Hotfix)

## Bugfixes

    - Programm crashing on Syncing Table contents in checklist. Now the Table is just being copied entirely.

# v1.2.1 (Hotfix)

## Bugfixes

    - Project filtering now removed full names, only displaying the projects identifier number
        Also fixed the problem with filtering by project and status.

# v1.2.0

## Features

### Added
    
    - Git Updater to pull newest release from git instead of local drive

# v1.1.0

## Features

### Added
    
    - Tooltips for table headers are now combined and shown as "?" next to table name marked as red
    - Number of found Readers are now displayed: "(n)"
    - More logging information to file
    - Converting older history .csv files to usable .json (csv has to be exported as UTF-8)
    - History window for sales and techsupport to browse older services and recent
    - History window table is saved to ImGui.ini so resized columns are loaded as they were closed
    - Way more logging to file / console
    - Only one instance of the programm can now be opened.
        The second instance will bring the first into foreground and focuses it.

### Removed

    - Table settings for checklists are no longer saved in ImGui.ini as it was just
      filling up the file

## Changes

    - Combo for Project search now sorts the projects ascending
    - Reader registry is now multithreaded. Is it faster? idk
    - Saving the checklist first tries to Sync it.
        May be slower but more save when 2 working on the same section

## Bugfixes

    - Crashes are now properly saved due to replacing Y: path to Y.
    - Docked and focused windows are now loaded correctly from savefile

# v1.0.1 (Hotfix)

## Bugfixes

    - Open checklist now saved on close

# v1.0.0

## Features

### Added

    - New Window to edit user accessibility on the fly instead of hardcoded
    - It is now possible to create and edit reader configs right away instead of manually creating them

## Changes

    - Complete visual overhaul
        - Drag and dropable windows
        - Closable windows
        - Dockable windows
    - Completely new framework
        - Easier to maintain in the future
        - Easier to add new functionality quick
        - Fileloading and saving using json
        - Old filedialog (.txt) still supported for reviewing
            (Handle with care and report crashes)
        - Clear structure of who has access to which functionality
    - Service Creator window now holds all service functionalities by itself

## Bugfixes

    - Changing a type from TEXTBOX to STRING is now possible. it resets multiline to false now

# v0.3.1

## Features

### Added
    
    - Crashes are now saved on WORKING_DIRECTORY/crashes/crash_yyyy-mm-dd hh-MM-ss.txt
    - New button to create service record (will be saved and opened locally)
    - Optional popups for sections when finishing (Just to display infotext)
    - HTML Export now takes style file from working directory
    - Readerstatus
        - Can be triggered and updated via sections of checklists
        - "erwartet" can be triggered if a reader is not in house
        - Can be filtered in reader selection
    - For double fields there can now be an fmt set for giving it values and making printout more flexible
        - Example: "%.4fM" makes 1000.0 -> 1000.0000M
    - Same tabs are now merged so no more different tabs per group 
        just "Checkliste", "ServiceCreator" and "Checklist Creator"

### Removed

    - Button "Zum Service hinzufügen", should have never been used. just for testing purpose or readers in house that were not tracked yet

## Changes

    - Mutiline task names now get printed on servicerecord
    - Changed empty boxes on servcierecord to red X
    - Better readability on printout for numbers and integers
        1000 becomes: 1.000
        1000,15 becomes: 1.000,15
    - Reparaturgeräte BMG only visible for TechSupport
    - On checklist creator made it easier to edit sections
    - New overlay on editing and creating tasks with more functionality and less boilerplate
    - Inputfields now resize automatically depending on the inserted content
    - New Singleton container to store already searched readers for faster lookup
    - Textboxes now resize according to newlines and text width
    - Using fallback_Checklist.txt for unavailable projects

## Bugfixes

    - String timestamps now get updated properly since they were never updated without enter
    - Timestamps now take localtime instead of basic UTC
    - SaveChecklist(checklist) now has a fallback to try using fl::u8topath() if file(path) does not exist and checks again with alternative path

# v0.3.0

## Features

### Added

    - Added xlnt for excel overview list

## Changes

    - Translated everything in German
    - On servicerecord output added proper page break for each section to not split them inbetween

## Bugfixes

    - Installer path still leading to TechSupport folder

# v0.2.6

## Features

### Added

    - New user setting to edit finished sections (Only editable for powerusers)
    - New user setting to edit sections they don't have permissions on (Only editable for powerusers)

### Removed
    
    - No english translation file generated anymore as it doesnt work anyways (yet)
        And just increases finish time

## Bugfixes

    - Pressing Tab on an integer or double field deleting inserted value

# v0.2.5

## Features

### Added

    - New user setting to hide poweruser functionality (Only editable for powerusers)
    - Tooltip per item, can be set as poweruser at Checklist Creator. Shows when hovering over an item
    - It is now possible to navigate through tables with enter and shift+enter
    - Pressing enter in the last row of a table adds another new row and jumps with cursor in new row

## Bugfixes

    - Comments were loaded incorrectly since they created a newline on each load
    - Going below 0 in table size crashing the programm upsi :)

# v0.2.4

## Features

### Added

    - A new button "Anleitung öffnen" to open user guidance (Taskbar upper window)

## Changes

    - Tables can now be properly edited in Checklist Creator

## Bugfixes

    - Checklist reloading on file dropping causing progress to be deleted
    - Some smaller fixes

# v0.2.3

## Features

### Added

    - qcs section in paths so they can be permissioned aswell

## Changes

    - Cleaned up the codebase to improve readability
    - layout -> moved tab items below Reader Overview and kept Reader Overview open at all times
    - icon changed
    - name changed from "ServiceCreator" to "ServiceTracker"
    - When finishing a checklist -> remove reader from open list and copy files in reader folder

## Bugfixes

# v0.2.2

## Bugfixes

    - Fixed programm crashing on Create Servicefolder

# v0.2.1

## Bugfixes

    - Fixed syncig files as they were not saved on changing reader

# v0.2.0

## Features

### Added

    - User settings to customize window behavior
    - Startup window (can be turned off in settings on the taskbar)
    - Checklists are fully implemented
        - Sections that can be permissioned to specific users
            - single line element
            - line with multiple elements
            - tables
            - Possible variable types:
                - Checkbox (True/False)
                - Integer (Numbers)
                - Floats (Floating numbers)
                - Text (Single line)
                - Textbox (Multi line)
                - Combobox (Drop down selectable)
        - create file requirements to fulfill and autotick checkbox
        - Automatic checklist copy when creating a new service for a reader
        - User informations for edited tasks
        - Syncing Checklists
        - Permissions per checklist sections
        - Permissions per checklist
        - Attachments saved on sync folder
        - Exportable as .csv for readability without the tool
    - Changed tool working directory to pool folder

## Changes

    - When reader gets added to list and no service selected, take last element in service lists
    - User specific interface tabs so no confusion between different sections
    - Moved "Create Servicefolder" to be right below reader selection

## Bugfixes

    - No more crashes when access to directories are denied, a warning is printed instead

# v0.1.1

## Features

### Added

    - Submitting changes that should be done with the ability to add subject, infotext and additional files

## Bugfixes

    - Bug fixed where there was no way to get back from submit window

# v0.1.0

## Features

### Added

    - search for readers in Gerätenachweise
    - create service folders with template files
    - add and remove readers from the open service list
    - drag and drop files directly into service folder 
    - drag drop changes file names when dropped
    - syncing open readers live
    - opening files and folders directly from ServiceCreator
    - Added Luke Filewalker to browse readers files and folders

# TODO

## Features

### Adding

    - External service functionality

### Removing

## Changes

## Bugs

