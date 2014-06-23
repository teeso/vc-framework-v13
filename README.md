# VC_Framework v13

> ## IMPORTANT NOTE
> 
> VC_Framework v13 is unlikely to receive further updates. I have a decent amount of work to do to fully support VC_Forms (which requires 4D v14) and there's no reason to make these changes in the v13 version. Plus there are some v14 features I would like to take advantage of.  So future development will be happening in the [VC_Framework v14 component](https://github.com/4D/vc-framework-v14) only.

## Description

The VC_Framework component facilitates automatic export of all methods in a [4D](http://www.4d.com) host database to text files on disk.  If the host database is under revision control, these text files are suitable for committing to the repository, thus giving the developer to ability to track changes to methods over time. Most importantly, the VC_Framework component is designed to have zero impact on the host database.  There is no startup code to install and nothing to configure.


## Contents

* The [Components](https://github.com/4D/vc-framework-v13/tree/master/Components) folder contains:
    * The "VC_Framework.4dbase" component suitable for installation in any [4D v13](http://www.4d.com/products/4dv13.html) database.
    * The "prog.4dbase" component, which extends 4D's Progress module to include a threshold for progress bar display. 
* The [matrix](https://github.com/4D/vc-framework-v13/tree/master/matrix) folder contains the component source code.


## Usage

Install the component (do NOT install an alias, you must install the component), launch the host database in 4D, and open a method if none are open. This will launch the stored procedures to manage method export.

(Optional) Install the "prog.4dbase" component. VC_Framework will not show progress bars without this component.

*Note: the first export may take some time in larger databases, but you only need to do this once.*

*Note: in a sufficiently complex database, VC_Framework may cause Design Mode to periodically hang. The component will detect this automatically and will let you know if it appears to be a problem.*


## Advanced Usage

### Activation at startup

Instead of waiting for VC_Framework to launch via method editor macros, you can install explicit startup code.  There is a macro for this; "VC_Framework: Startup Install - Optional".

### Process Management

The processes that handle exporting or deleting methods can be managed via macros. For example you can start or stop the process via macros. These macros are visible in your macros menus.

### Advanced configuration

There are several shared "setter" methods that allow you to tweak the component (methods named VC_CONFIG_*Set). Reminder: the component is open source, if you are interested in these settings look at the source code to see what they do. Ideally the component should function without any tweaks (that's the goal). If you find you need to change something, please [let me know](mailto:jfletcher@4d.com).

### RC Integration Hooks

The VC_Framework component can be extended to support revision control (RC) integration. If the host database (or another component) contains the following shared methods

* VC_DEVHOOK_Create
* VC_DEVHOOK_Update
* VC_DEVHOOK_Delete

The VC_Framework component will call these methods prior to saving/deleting the method. The callee can choose whether or not to allow the save as well as take any action necessary to notify the RC software of the change.

The [VC_SVN](https://github.com/4D/vc-svn-v13) component is an example of this.