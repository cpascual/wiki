---
title: NXentry
permalink: NXentry/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXentry.xml
    Editor:  NIAC
    NIAC Version: 1.0
    $Id$

    Template of the top-level NeXus group which contains all the data and
    associated information that comprise a single measurement. It is mandatory 
    that there is at least one group of this type in the NeXus file.

    -->
    <NXentry name="{Entry Name}">
        <title>
            {Extended title for entry}?
        </title>
        <definition version="{DTD version number}" URL="{URL of DTD file}">
            {Name of entry DTD}?
        </definition>
        <start_time type="ISO8601">
            {Starting time of measurement}?
        </start_time>
        <end_time type="ISO8601">
            {Ending time of measurement}?
        </end_time>
        <duration type="NX_INT">
            {Duration of measurement}?
        </duration>
        <experiment_identifier type="NX_CHAR">
            {}?
        </experiment_identifier>
        <run_number type="NX_INT">
            {Number of run or scan stored in this entry}?
        </run_number>
        <run_cycle type="NX_CHAR">
            {Number of the facility cycle in which the measurements were made}?
        </run_cycle>
        <program_name version="{Program version number}">
            {Name of program used to generate this file}?
        </program_name>
        <command_line>
            {Name of command line used to generate this file}?
        </command_line>
        <notes>
            {Notes describing entry}?
        </notes>
        <thumbnail type="NXnote">
            {An small image that is representative of the entry.} {An example of this is a 640x480 jpeg image automatically produced by a low resolution plot of the NXdata.}?
        </thumbnail>
        <NXuser name="{user}">
            *
        </NXuser>
        <NXsample name="{sample}">
            ?
        </NXsample>
        <NXinstrument name="{Name of instrument}">
            ?
        </NXinstrument>
        <NXmonitor name="{Name of monitor}">
            *
        </NXmonitor>
        <NXdata name="{Name of data block}">
            *
        </NXdata>
        <NXprocess name="{Name of the process}">
            ?
        </NXprocess>
    </NXentry>
