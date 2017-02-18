---
title: NXsource
permalink: NXsource/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXsource.xml
    Editor:  NIAC
    $Id: NXsource.xml,v 1.3 2006/02/10 13:59:54 sic78 Exp $

    Template of the neutron or x-ray source, insertion devices and/or moderators.

    -->
    <NXsource name="source">
        <distance type="NX_FLOAT" units="m">
            {Effective distance from sample}{Distance as seen by radiation from 
                    sample.  This number should be negative to signify that it is upstream 
                    of the sample.}?
        </distance>
        <name type="NX_CHAR">
            {Name of source}?
        </name>
        <type type="NX_CHAR">
            "Spallation Neutron Source"|"Pulsed Reactor Neutron Source"|
                    "Reactor Neutron Source"|"Synchrotron X-ray Source"|"Pulsed Muon Source"|
                    "Rotating Anode X-ray"|Fixed Tube X-ray"?
        </type>
        <probe type="NX_CHAR">
            neutron|x-ray|muon|electron?
        </probe>
        <power type="NX_FLOAT" units="MW">
            {Source power}?
        </power>
        <current type="NX_FLOAT" units="microamps">
            {Accelerator current}?
        </current>
        <voltage type="NX_FLOAT" units="MeV">
            {Accelerator voltage}?
        </voltage>
        <frequency type="NX_FLOAT" units="Hz">
            {Frequency of pulsed source}?
        </frequency>
        <period type="NX_FLOAT" units="microseconds">
            {Period of pulsed source}?
        </period>
        <target_material type="NX_CHAR">
            {Pulsed source target material} 
                    {"Ta"|"W"|"depleted_U"|"enriched_U"|"Hg"|"Pb"|"C"}?
        </target_material>
        <notes type="NX_CHAR">
            {any source/facility related messages/events that occurred during the 
                    experiment}?
        </notes>
        <pulse_width type="NX_FLOAT" units="micro.second">
            {width of source pulse}?
        </pulse_width>
        <pulse_shape type="NXdata">
            {source pulse shape}?
        </pulse_shape>
        <mode type="NX_CHAR">
            {synchrotron operating mode}{"Single Bunch"|"Multi Bunch"}?
        </mode>
        <top_up type="NX_BOOLEAN">
            {Is the synchrotron operating in top_up mode}?
        </top_up>
        <NXgeometry name="">
            {"Engineering" location of source}?
        </NXgeometry>
    </NXsource>
