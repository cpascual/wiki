---
title: Processed Data
permalink: Processed_Data/
layout: wiki
---

    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXprocessed.xml
    Editor:  NIAC
    NIAC Version: 0.1
    $Id$

    Template of a generic NXentry containing processed data.  

    The assumption is that measured data, which could, for example, stored in another 
    NXentry within the same file, has been reduced to a standard form, e.g., S(Q), so 
    that the instrument information is no longer required.  It is only necessary, therefore,
    to store the multidimensional array containing the processed data within one or more
    NXdata groups.

    This is not a true metaDTD because both the values and the axis names can use 
    something more descriptive.

    -->
    <NXentry name="{Name of entry}">
      <title>
        {Extended title for entry}
      </title>
      <definition URL="http://www.nexus.anl.gov/instruments/xml/NXprocessed.xml"
          version="1.0">
        NXprocessed
      </definition>
      <NXsample name="{name of sample}">?
        {Any relevant sample information necessary to define the data.}
      </NXsample>
      <NXdata name="{Name of processed data}">
        <values signal="1" type="NX_FLOAT[:,:]" axes="axis1:axis2">{Processed values}</values>
        <axis1 type="NX_FLOAT[:]">{Values of the first dimension's axis}</axis1>
        <axis2 type="NX_FLOAT[:]">{Values of the second dimension's axis}</axis2>
      </NXdata>
    </NXentry>