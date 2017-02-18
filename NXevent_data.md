---
title: NXevent data
permalink: NXevent_data/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXevent_data.xml
    Editor:  NIAC
    $Id: NXevent_data.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of NXevent_data

    -->
    <NXevent_data name="">
        <time_of_flight type="NX_INT[i]" units="10^n second">
            {A list of time of flight for each event as it comes in. This list is 
            for all pulses with information to attach to a particular pulse located 
            in events_per_pulse.}?
        </time_of_flight>
        <pixel_number type="NX_INT[i]">
            {There will be extra information in the NXdetector to convert 
            pixel_number to detector_number. This list is for all pulses with 
            information to attach to a particular pulse located in 
            events_per_pulse.}?
        </pixel_number>
        <pulse_time type="NX_INT[j]" offset="{ISO8601}" units="10^n second">
            {The time that each pulse started with respect to the offset}?
        </pulse_time>
        <events_per_pulse type="NX_INT[j]">
            {This connects the index "i" to the index "j". The jth element is the 
            number of events in "i" that occured during the jth pulse.}?
        </events_per_pulse>
        <pulse_height type="FLOAT[i,k?]" units="">
            {If voltages from the ends of the detector are read out this is where 
            they go. This list is for all events with information to attach to a 
            particular pulse height. The information to attach to a particular pulse 
            is located in events_per_pulse.}?
        </pulse_height>
    </NXevent_data>
