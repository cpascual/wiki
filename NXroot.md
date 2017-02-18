---
title: NXroot
permalink: NXroot/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXroot.xml
    Editor:  NIAC
    $Id: NXroot.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Definition of the root NeXus group.

    -->
    <NXroot file_name="{File name of original NeXus file}" 
            file_time="{Date and time of file creation}" 
            file_update_time="{Date and time of last file change at close}" 
            NeXus_version="{Version of NeXus API used in writing the file}" 
            HDF_version="?" 
            HDF5_version="?" 
            creator="{facility or program where file originated}?">
        <NXentry name="{entry name}">
            +
        </NXentry>
    </NXroot>
