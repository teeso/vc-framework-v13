# VC_Framework

## Description

The VC_Framework component facilitates automatic export of all methods in a [4D](http://www.4d.com) host database to text files on disk.  If the host database is under revision control, these text files are suitable for committing to the repository, thus giving the developer to ability to track changes to methods over time. Most importantly, the VC_Framework component is designed to have zero impact on the host database.  There is no startup code to install and nothing to configure.

The VC_Framework component can be extended to support revision control (RC) integration. If the host database (or another component) contains the following shared methods

* VC_DEVHOOK_Create
* VC_DEVHOOK_Update
* VC_DEVHOOK_Delete

The VC_Framework component will call those methods prior to saving/deleting the method. The callee can choose whether or not to allow the save as well as take any action necessary to notify the RC software of the change.

## Contents

* The [Components](VC_Framework/tree/master/Components) folder contains the interpreted component suitable for installation in any [4D v13](http://www.4d.com/products/4dv13.html) database.
* The [matrix](VC_Framework/tree/master/matrix) folder contains the component source code.
* The [doc](VC_Framework/tree/master/doc) folder contains documentation about the component.

## Usage

If you modify the matrix database, you should build a new component.  To build a new component, execute the BLD_Build method from the matrix database.
