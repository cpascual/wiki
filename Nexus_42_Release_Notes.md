---
title: Nexus 42 Release Notes
permalink: Nexus_42_Release_Notes/
layout: wiki
---

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

Building Notes
--------------

### NAG F90/F95 Compiler

The NAG compiler needs the **-mismatch** flag to be specified or else it
will not compile NXmodule.f90 This is achieve by running configure with
the **FCFLAGS** environment variable set to contain the flag e.g.

    env FCFLAGS="-mismatch" ./configure --with-f90=f95

### HDF4 on Intel Macs

There is a problem with the include file, hdfi.h (normally in
/usr/local/include). See
<http://coastwatch.noaa.gov/helparc/software/msg00069.html> for details
of the modifications necessary to fix it.

New Features
------------

Changed Features
----------------

Known Issues
------------

Miscellaneous bug fixes
-----------------------

The following items are bugs reported in previous releases and resolved
in the 4.2 release.

Upcoming Features
-----------------