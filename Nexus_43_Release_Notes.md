---
title: Nexus 43 Release Notes
permalink: Nexus_43_Release_Notes/
layout: wiki
---

4.3.0
-----

New Features
------------

-   Links to external files via the NeXus external linking mechanism
    have now been enhanced to take advantage of native HDF5 external
    linking. Previously a nexus external file link was only visible to
    NeXus aware programs, and this will continue to be the case for XML
    and HDF4 based files. In the case of files created with the HDF5
    underlying format, external file links will now be visible to any
    HDF5 (1.8.\*) aware program.
-   HDF5 based files can now have multiple “unlimited” dimensions
    (previously only one was allowed)
-   New API functions have been added to handle very large arrays. Most
    origial nexus functions had array dimensions of type “int” which
    restricted the maximum size of an array. New functions with a “64”
    suffix have been added which use int64\_t rather than int.
-   A new python tree API has been added
-   A GUI java based NXvalidate program has now been added

Changed Features
----------------

-   The HDF5 1.6.\* series libraries are no longer supported - NeXus now
    requires 1.8.\* or higher. The 1.6.\* series is now very old and
    moving to 1.8.\* has allowed us to make use of new and improved
    features, such as native external file linking (see above)

System Requirements
-------------------

**MXML XML Parsing Library**

Version 2.2.2 or higher of mxml is required. Earlier versions have a bug
and the XML API will not work. This package can be downloded in [both
source and binary rpm
form](http://www.easysw.com/~mike/mxml/software.php) and is also
available as part of [Fedora
Extras](http://fedoraproject.org/wiki/Extras/UsingExtras). IMPORTANT
NOTE: Debian also provides the mxml package, but it based on 2.0 and
will not work properly.

**Python Interface** You will need both the numpy and ctypes modules to
be available. These are provided in both the Fedora and EPEL
repositories.

**HDF5 Version** Only the HDF5-1.8.\* series (and above) is now
supported.

Building Notes
--------------

Known Issues
------------

Miscellaneous bug fixes
-----------------------

Upcoming Features
-----------------