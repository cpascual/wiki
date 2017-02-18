---
title: NXlog
permalink: NXlog/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXlog.xml
    Editor:  NIAC
    $Id: NXlog.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Definition of logged information, i.e. information monitored during the run.
    They contain the logged values and the times at which they were measured as
    elapsed time since a starting time recorded in ISO8601 format. This method of
    storing logged data helps to distinguish instances in which a variable is a
    dimension scale of the data, in which case it is stored in an NXdata group, and
    instances in which it is logged during the run, when it should be stored in an
    NXlog group.

    -->
    <NXlog name="{Name of logged measurements}">
        <time start="{ISO8601}" units="" type="NX_FLOAT">
            {Time of logged entry}{The times are relative to the "start" attribute 
            and in the units specified in the "units" attribute.}
        </time>
        <value units="{units of logged value}" type="NX_FLOAT|NX_INT">
            {Array of logged value, such as temperature}
        </value>
        <raw_value units="{units of raw values}" type="NX_FLOAT|NX_INT">
            {Array of raw information, such as voltage on a thermocouple}?
        </raw_value>
        <description type="NX_CHAR">
            {Description of logged value}?
        </description>
        <average_value type="NX_FLOAT" units="">
            ?
        </average_value>
        <average_value_error type="NX_FLOAT" units="">
            {standard deviation of average_value}?
        </average_value_error>
        <minimum_value type="NX_FLOAT" units="">
            ?
        </minimum_value>
        <maximum_value type="NX_FLOAT" units="">
            ?
        </maximum_value>
        <duration type="NX_FLOAT" units="">
            {Total time log was taken}?
        </duration>
    </NXlog>
