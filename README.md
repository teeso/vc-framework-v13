# VC_Framework v13

## Description

The VC_Framework component facilitates automatic export of all methods in a [4D](http://www.4d.com) host database to text files on disk.  If the host database is under revision control, these text files are suitable for committing to the repository, thus giving the developer to ability to track changes to methods over time. Most importantly, the VC_Framework component is designed to have zero impact on the host database.  There is no startup code to install and nothing to configure.

The VC_Framework component can be extended to support revision control (RC) integration. If the host database (or another component) contains the following shared methods

* VC_DEVHOOK_Create
* VC_DEVHOOK_Update
* VC_DEVHOOK_Delete

The VC_Framework component will call these methods prior to saving/deleting the method. The callee can choose whether or not to allow the save as well as take any action necessary to notify the RC software of the change.

## Contents

* The [Components](https://github.com/4D/vc-framework-v13/tree/master/Components) folder contains the "VC_Framework.4dbase" component suitable for installation in any [4D v13](http://www.4d.com/products/4dv13.html) database.
* The [matrix](https://github.com/4D/vc-framework-v13/tree/master/matrix) folder contains the component source code.

## Usage

Install the component (do NOT install an alias, you must install the component), launch the host database in 4D, and open a method if none are open. This will launch the stored procedure to manage method export.

Note: the first export may take some time in larger databases, but you only need to do this once.

If you modify the matrix database, you should build a new component.  To build a new component, execute the BLD_Build method from the matrix database (the matrix database uses the ["BLD.4dbase" component](https://github.com/4D/interpreted-build-v13)).
