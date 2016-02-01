![](sigasi_logo.png)

# Sigasi Training

## Setup

Requirements:

  * Sigasi 3.0.1
  * valid Sigasi (XL-DOC) license file
  * Training VHDL sources (see below)

Get the training sources:

* Download the source files from <https://github.com/sigasi/sigasi_training/archive/master.zip>
* Unzip

You can find the files for each part in the corresponding folder. 

The VHDL source files contain `TODO` comments, which explain the tasks of the exercises. This document is an extra tool to guide you trough the exercises. It also helps you to keep track of your progress.


|       | Agenda                |
| ----- | :-------------------- |
| 9:00  | General Introduction  |
| 9:15  | Part 1: VHDL Files    |
| 10:45 | break                 |
| 11:00 | Part 2 : VHDL projects|
| 12:30 | Lunch break           |
| 13:30 | Part 3 : Linting and other features|
| 15:00 | break                 |
| 15:15 | Part 4 : Hierarchy, Graphics and documentation|
| 16:45 | Recap and Q&A         |
| 17:00 | End                   |


<p style="page-break-after:always;"></p>

## Part 1: VHDL files

The goal of the first part is to get comfortable with the Sigasi VHDL editor. By the end you should be able to _easily detect and fix VHDL syntax issues_, _customize editor preferences_ and _know the basic keyboard shortcuts_.

### Edit

* Open file `part1_edit.vhd` via **File > Open File...**
* Make the editor _full screen_ (Double click the tab)
* Double click again to exit _full screen_ mode
* Format the VHDL code (**Ctrl+Shift+F**, _Make sure no text is selected_)
* Fix all VHDL syntax issues, use the QuickFix where possible (When in doubt, **Hover** the error Marker)

* Delete a line with **Ctrl+D**
* Comment a line with **Ctrl+/**
* Move a line up and down with **Alt+Up** and **Alt+Down**
* Autocomplete (**Ctrl+Space**)
  * Name
  * Constant declaration  
  * `if` statement in a `process` (Use **enter** to exit the _template mode_)
  * `if generate` in an `architecture`  
* Block select (**Shift+Alt+A**, or button in toolbar)
  * Delete a Block
  * Add content on multiple lines 
* Enable _Show whitespace_ (¶-button) and type some _tabs_ and _spaces_ to see the difference
* Find & Replace  
	* Experiment with **Ctrl+F**, e.g. find all `TODO`'s
	* Use **Ctrl+K** to find the next occurrence of the current selection
	* Use **Ctrl+J** (and start typing) for an inline, incremental search. _Look at the status bar to see what you have already typed_.
* Use **Quick Access** to convert an identifier to UpperCase (Select the identifier, type `upper` in the Quick Access Field in the Toolbar and confirm with **Enter**)
* Mess up part of the source code, select it and **format only the selection**.

### Navigate

* Open file `part1_navigate.vhd` via **File > Open File...**
* Open Declaration  (**F3**)
* Move back to last location (**Alt+Left**)
* Go to Line  (**Ctrl+L**)
* Navigate to errors with the gutter (Click red rectangles in scroll bar)
* Navigate to next problem marker (**Ctrl+.**)
* Navigate with the *Outline view*

### Customize settings

Preferences can be set via **Window > Preferences**.
* Open file `part1_custom.vhd`
* Switch to VHDL 2008 (**Preferences > Sigasi > VHDL**) and check the syntax error get resolved
* Tabs or spaces ( Use the search box in the preference dialog and type `tab`) Use _Show whitespace_ to check.
* Uppercase keywords (**Preferences > Sigasi > VHDL > Formatting**) (Use _format_ to check)

### Extra tasks

* Open file `part1_extra.vhd`
* *Stuttering* (double tap the `.`, `:` or `,` key)
* Try *structured select* <http://insights.sigasi.com/manual/editor.html#structured-selection>
* Remove trailing whitespace (Use **Quick Access** to find and run this action)
* Drag and drop a file from your file explorer in Sigasi  
* Create a new file  (**File > New External File**)
* Outline: Figure out what *Link with editor* button (⇆) does
* Add a keyboard shortcut preference for _show whitespace_ (Search for the **Keys** preference page)

<p style="page-break-after:always;"></p>

## Part 2: VHDL projects

The goal of Part 2 is to understand what a project is, why you want projects and how to set one up. You will learn how to add files to your projects and make sure the VHDL library is correctly setup.

As an extra, you will how to efficiently work with Finite State Machines.

### Setup

* Switch to the **Sigasi** perspective (Button in top right) 
* Import project `part2_vhdl_project`
  1. **File > Import...**
  2. **Existing project into Workspace**, **Next**
  3. **Browse** to `part2_vhdl_project`
  5. **Finish**

### Navigation

* Open `navigation.vhd` with **Open Resource** (**Ctrl+Shift+R**) or via the Project Explorer
  * Project Explorer: Enable the *Link with editor* button (⇆)
  * Hover `MAX_COUNT`
  * Open declaration of `std_logic` and other declarations
  * Navigate back (**Alt+Left**)

* Open `components.vhd`
  * Navigate to Entity from Component instantiation (**Ctrl+Click** or **Shift+F3**)
  * Find References of port `rst`
  * Open two editors side by side (Drag editor tab)

* Navigate through the project with the following Views: (If they are not visible, open them with **Quick Access**)
  * Libraries View
  * Problems View
  * Task View
  * Dependencies View

### Edit 

* Open file `edit.vhd`
* Use Quickfix to fix the invalid sensitivity list

### Libraries

* Open `libraries.vhd`
* Set folder `my_lib` to library `my_lib` (Project explorer: **Set Library**)

### State machines:

* Open file `fsm.vhd`
* Declare enum type `state_type`: (`start`, `running`, `ready`)
* Declare signal `state` of `state_type`
* Autocomplete `case statement`
* Add some transitions
* Add case choice `when idle` and use quickfix to add enum literal to enum type (QuickFix)
* Remove case choice `when idle` and use the quickfix on `case state` to add it again.
* **Ctrl+Click** on a state assignment and select **Open Matching when Clause**. 

### Rename

* Manual rename: Change (edit) `port_1` to `port_1a` and manually update the matching instantiations
* Rename (**Refactor > Rename element**) port `port_a` to `port_aa`
* Compare file with *Local history* (Right-click on file, **Compare With > Local History...**) and inspect the changes you made

### Import (non-Sigasi) project + setup libraries

* First: Check that your are VHDL 2008 mode
* **File > Import...**
* **Sigasi > Import a VHDL project**, **Next \>**
* **Browse...** to `vunit_example`, **Finish**
* Set the project to library `uart_lib` (right click, **Set Library**)  
  Check the library annotations in the project explorer
* Import library `vunit_lib`:
  * Drag and drop the `vunit_lib` folder into the `Common Libraries` folder. Choose the option to _link to files and folders_.
  * Set the library to `vunit_lib`  
* Set the library for the test files (`uart/src/test`). Read the source code for the library name.
* One more library is not correctly set. Try to fix this. (Tip: the sources are already in the project)

### Extra Tasks

* Select `edit.vhd` and `navigate.vhd` and compare them via the right click menu.
* Configure and enable an External Compiler (See `extra_compiler.vhd`)
* Set the top level and start the Simulator (See `extra_compiler.vhd`)
* Export a CSV file with all files in your project (**File > Export... > Sigasi > CSV file**)

<p style="page-break-after:always;"></p>

## Part 3: Linting and other features

In Part 3 you will learn more about VHDL linting (code checks) and how you can get to zero warnings.

We will also explore other, generic Sigasi/Eclipse features.

### Linting

* Import Project `part3`
* Close unrelated projects (Right Click project in Project Explorer)
* Fix all **Errors** (Track your progress in the Problems View)
* Fix all `--TODO: fix` **Warnings** (Track your progress in the Task View)
* Change the severity of the **Check for position associations in instantiations** linting via the Preferences (**Sigasi > VHDL > Errors/Warnings**). Set to severity to **Error**. Check that the warnings are now errors.

### Waive specific warnings

* Open `waive.vhd`
* Suppress the *Null Range* warning by adding
 ```
 -- @suppress
 ```  
 **Note:** You need to save before the warnings are really suppressed.
* Check that the warning marker is removed from the **Problems View**
* Explicitly specify which warning you suppress by adding the warning message prefix:
 ```
 -- @suppress "Null Range"
 ```
* Verify that the warning marker re-appears when you type another prefix
* Now also explain why you suppress the warning by adding an explanation:
 ```
 -- @suppress "Null Range" Ok here, see http://...
 ```
 
### Other features

* Project Explorer
  * Show hidden files (Click **▿**, **Customize view**, disable the `.* resources`)
  * Delete and restore a file from local history (Right click and **Restore from Local History...**)	
* Bookmarks:
  * Right click a line number and select **Add Bookmark**
  * Open the bookmark view
* Multiple screen support
  1. Open a new Window (**Window > New Window**)
  2. Drag the new windows to a different screen
* Customize Autocomplete templates: Add a custom header to the `entity/architecture pair` template:
  1. **Window > Preferences > Sigasi > VHDL > Templates**
  2. Select **entity/architecture pair**
  3. Click **Edit...**
  4. Add a custom header (e.g. `-- Confidential, Copyright 2016`)
  5. Confirm with **OK**
  6. Create a new VHDL and select your customized template (**File > New > VHDL file**, choose a name, **Next** and choose the `entity/architecture pair` template)

### Extra tasks

* Customize your perspective:
  1. **Window > Perspective > Customize Perspective...**
  2. Enable the **Print** button in **File**
* Configure the **Naming Convention** settings to check for *Uppercase* constants (`[A-Z_]+`)
* Open and explore the Properties Page (Right click file, **Properties**)
* Multiple Search Views
  1. Run a first search (e.g. Find Reference on `std_logic`)
  2. Click the **Pin the Search View** button
  3. Start a new search. This search will open in a new _Search View_
* Configure project specific settings <http://insights.sigasi.com/manual/linting.html#project-specific-linting-settings>
  
<p style="page-break-after:always;"></p>
  
## Part 4: Hierarchy, Graphics and documentation

In Part 4 you will learn how to use the Hierarchy View. You will also learn how to use and export Graphics and Documentation with Sigasi.

### Hierarchy View

* Import project `part4` (and close unrelated projects)
* Open `testbench.vhd`
* Right click the `STR` architecture and select **Set as Top Level**
* Explore the resulting tree in the Hierarchy View:
  * Inspect the value of generics (Notice how the value in `dut_instance` differs from its default value)
  * Change some generics and see how the Hierarchy View is refreshed when you save.
  * Add some syntax errors and verify that Sigasi is able to recover and still show valid content in the Hierarchy View
  * Disable the **Toggle Hierarchy Refresh** toggle button, and notice Sigasi no longer auto-updates the hierarchy when edit your files. (This is useful for big hierarchies)

### Block Diagram View

* Open `testbench.vhd`
* Right click the VHDL editor and select **Show in > Block Diagram**
* Double click ports or connections to navigate to the corresponding VHDL code. (This also works the other way around by clicking **Show in > Block Diagram** on ports in the VHDL code)
* Make some changes in the VHDL code and see how the Block Diagram updates when you save your file.
* Select `dut_instance` in the diagram, right click and select **Open Entity Declaration** to navigate to the corresponding entity, `dut`.
* Click the save icon (	💾), and export the diagram to an SVG or PNG file.

### State Machine View

* Open `dut.vhd`
* Right click the vhdl editor and select **Show in > State Machines**
* Double click a few ports and transitions to navigate to the corresponding VHDL code.
* Change the VHDL code of the state machine and notice how the view updates (See TODO tag)
* Add a comment to the `when idle: state := preparing;` transition. e.g. `-- start preparing`  
  Notice how the transition labels update
* Toggle the (Aa)-button to show/hide the transition labels.
* Click the save icon (💾), and export the diagram to file.

### Documentation

* Import project `Sigasi_doc`
* Open the Documentation View
* Open file `testbench.vhd`
* Edit comments and see how the documentation is updated:
  * Document a port (by adding a comment)
  * Document a generic
  * Document an architecture
  * Document an entity
* Export PDF
* Inspect the DocBook file

### Extra tasks

* Try out **Net search** in `stimgen.vhd` (Project `part4`)
* State Machine View: Add a second state machine in `dut.vhd` and see how it is displayed in a new tab.
* Finish the documentation of the Project to get a clean and complete PDF.

<!--
* Modify the documentation templates:
  * Copy the templates from the Installation (`<installation folder>/plugins/com.sigasi.hdt.docgen.resources_.../templates`) to your workspace (`<workspace folder>/sigasi-templates`)
  * Modify the `preview.xml` template and inspect the result in the **Documentation View**
-->

<p style="page-break-after:always;"></p>

# Troubleshooting

* Where are my views? → **Window > Perspective > Reset perspective**
* Unexpected error markers? → **Project > Clean...**
* Error markers are not updated? → Make sure **Automatic build** is enabled
* More on <http://insights.sigasi.com/manual/trouble.html>


---
Copyright Sigasi NV 2016
