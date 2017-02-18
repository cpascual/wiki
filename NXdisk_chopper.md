---
title: NXdisk chopper
permalink: NXdisk_chopper/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXdisc_chopper.xml
    Editor:  Mark Koennecke
    $Id: NXdisk_chopper.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of NXdisc_chopper.

    -->
    <NXdisk_chopper name="{chopper_name}">
        <type type="NX_CHAR">
            {Chopper type single|contra_rotating_pair|synchro_pair}?
        </type>
        <rotation_speed type="NX_FLOAT" units="rpm|hertz">
            {chopper rotation speed}? 
        </rotation_speed>
        <slits type="NX_INT">
            {Number of slits}
        </slits>
        <slit_angle type="NX_FLOAT" units="degree">
            {angular opening}
        </slit_angle>
        <pair_separation type="NX_FLOAT" units="cm">
            {disc spacing in direction of beam}?
        </pair_separation>
        <radius type="NX_FLOAT" units="cm">
            {radius to centre of slit}
        </radius>
        <slit_height type="NX_FLOAT" units="cm">
            {total slit height} 
        </slit_height>
        <phase type="NX_FLOAT" units="degree">
            {chopper phase angle}? 
        </phase>
        <ratio type="NX_INT">
            {pulse reduction factor of this chopper in relation to other choppers
                    /fastest pulse in the instrument}? 
        </ratio>
        <distance type="NX_FLOAT" units="cm">
            {Effective distance to the origin}? 
        </distance>
        <wavelength_range type="NX_FLOAT[2]" units="nm">
            {low and high values of wavelength range transmitted}?
        </wavelength_range>
        <NXgeometry name="">
            {geometry of the disk chopper}?
        </NXgeometry>
    </NXdisk_chopper>
