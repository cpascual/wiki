---
title: NXdata
permalink: NXdata/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXdata.xml
    Editor:  NIAC
    $Id: NXdata.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of plottable data and their dimension scales. It is mandatory that
    there is at least one group of this type in each NXentry group.  Note that
    "variable" and "data" can be defined with different names.  The "signal" and
    "axes" attribute of the "data" item define which items are plottable data and
    which are dimension scales.

    -->
    <NXdata name="{Name of data block}">
        <variable type="NX_FLOAT[:]|NX_INT[:]" long_name="{Axis label}" 
                  distribution="0|1" first_good="{Index of first good value}" 
                  last_good="{Index of last good value}">
            {Dimension scale defining an axis of the data}?
        </variable>
        <variable_errors type="NX_FLOAT[:]|NX_INT[:]">
            {Errors associated with axis "variable"}?
        </variable_errors>
        <data type="NX_FLOAT[:...]|NX_INT[:...]" signal="1" axes="[...]" 
              long_name="{Title of data}">
            {Data values}?
        </data>
        <errors type="NX_FLOAT[:...]">
            {Standard deviations of data values - the data array is identified by 
            the attribute signal="1". This array must have the same dimensions as 
            the data}?
        </errors>
    </NXdata>
