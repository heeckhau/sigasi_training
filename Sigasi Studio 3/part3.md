## Part 3: Linting and other features

In Part 3 you will learn about VHDL linting (code checks) and how you can get to zero warnings.

We will also explore other features that are not specific to VHDL.

### Linting

* Import Project `part3`
* Close unrelated projects (Right Click project in Project Explorer)
* Fix all **Errors** (Track your progress in the Problems View)
* Fix all `--TODO: fix` **Warnings** (Track your progress in the Task View). We will get to the other warnings later.
* Change the severity of the **Check for position associations in instantiations** linting via the Preferences (**Sigasi > VHDL > Errors/Warnings**). Set to severity to **Error**. Note that this warning in the code is now an error.

### Custom problems view
* Open the **Problems View**
* Click on the triangle on the top-right of the view
* Select **New Problems View**
* Give it the name `Problems of this file`
* Move the view next to the original **Problems view**
* Click the triangle in your new **Problems view**
* Choose **Filters...**
* Untick **Show all items**
* Select only the Configuration **Errors/Warnings on Selection**
* Limit the scope to **On selected elements only**
* The new problems view will only show problems in the currently selected file.

### Waive specific warnings

* Open `waive.vhd`
* Suppress the *Null Range* warning by adding
 ```
 -- @suppress
 ```  
* The warning disappears shortly after typing the @suppress comment
* Note that the warning marker is removed from the **Problems View** once you save the file
* Explicitly specify which warning you suppress by adding the warning message prefix
 ```
 -- @suppress "Null range"
 ```
* Note that the warning marker re-appears when you type another prefix or make a typo
* Now also explain why you suppress the warning by adding an explanation
 ```
 -- @suppress "Null range" Ok here, see http://...
 ```

### VHDL version
 * Set the workspace VHDL version to '93 via the Preferences (**Sigasi > VHDL**) 
 * Open `version.vhd`
 * Review the errors
 * Change the VHDL version of the project
   * **Right-Click** on the project and select **Properties**
   * Change the version to 2008
 * Review the errors in `version.vhd`
 * Force a clean-build (**Project > Clean...**)
 * The project still uses the 93 libraries, replace them with the 2008 libraries by selecting **Right-Click project > Set Library > Reset Library Mapping**
 * All errors should fixed
  
### Other features

* Project Explorer
  * Show hidden files (Click **▿**, **Filters and Customization**, disable the `.* resources`)
  * Delete a file from your project. Next, restore this file from local history: In the Project Explorer, right click the project **Part3** and select **Restore from Local History...**
* Bookmarks:
  * Right click a line number and select **Add Bookmark**
  * Open the Bookmarks view (**Window > Show View > Other... > General > Bookmarks**)
* Multiple screen support
  1. Open a new Window (**Window > New Window**)
  2. Drag the new windows to a different screen
* Customize Autocomplete templates: Add a custom header to the `entity/architecture pair` template:
  1. **Window > Preferences > Sigasi > VHDL > Templates**
  2. Select **entity/architecture pair**
  3. Click **Edit...**
  4. Add a custom header (e.g. `-- Confidential, Copyright 2016`)
  5. Confirm with **OK**
  6. Create a new VHDL file and select your customized template (**File > New > VHDL file**, choose a name, **Next** and choose the `entity/architecture pair` template)

### Optional Extra tasks

* Customize your perspective:
  1. **Window > Perspective > Customize Perspective...**
  2. Enable the **Print** button in **File**
* Configure the **Naming Convention** settings to check for *Uppercase* constants (`[A-Z_]+`)
* Open and explore the Properties Page (Right click file, **Properties**)
* Multiple Search Views
  1. Run a first search (e.g. Find Reference on `std_logic`)
  2. Click the **Pin the Search View** button
  3. Start a new search. This search will open in a new _Search View_
* Configure project specific settings <https://insights.sigasi.com/manual/linting.html#project-specific-linting-settings>
* Expriment with customized Templates
  * Use different contexts: DesignFile, ConcurrentStatement, AnyWhere
  * Explore the pattern syntax by looking at the existing templates.
* Create a **Problems View** that only shows problems from the **External Compiler** in the selected Project
  
