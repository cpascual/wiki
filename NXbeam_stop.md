---
title: NXbeam stop
permalink: NXbeam_stop/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXbeam_stop.xml
    Editor:  Mark Koennecke
    $Id: NXbeam_stop.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    A class for a beamstop. Beamstops and their positions are important for SANS
    and SAXS experiments.
    -->
    <NXbeam_stop name="">
        <NXgeometry name="">
            {engineering shape, orientation and position of the beam stop.}?
        </NXgeometry>
        <description type="NX_CHAR">
            {description of beamstop: circular | rectangular}? 
        </description>
        <size type="NX_FLOAT" units="cm">
            {size of beamstop}? 
        </size>
        <x type="NX_FLOAT" units="cm">
            {x position of the beamstop in relation to the detector}? 
        </x>
        <y type="NX_FLOAT" units="cm">
            {y position of the beamstop in relation to the detector}? 
        </y>
        <distance_to_detector type="NX_FLOAT" units="cm">
            {distance of the beamstop to the detector} 
        </distance_to_detector>
        <status type="NX_CHAR">
            {in|out}? 
        </status>
    </NXbeam_stop>
