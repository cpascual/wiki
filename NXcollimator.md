---
title: NXcollimator
permalink: NXcollimator/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXcollimator.xml
    Editor:  NIAC
    $Id: NXcollimator.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of a beamline collimator.

    -->
    <NXcollimator name="{Name of collimator}">
        <NXgeometry name="">
            {position, shape and size}?
        </NXgeometry>
        <type type="NX_CHAR">
            "Soller"|"radial"|"oscillating"|"honeycomb"?
        </type>
        <soller_angle type="NX_FLOAT" units="minutes">
            {Angular divergence of Soller collimator}?
        </soller_angle>
        <divergence_x type="NX_FLOAT">
            {divergence of collimator in local x direction}?
        </divergence_x>
        <divergence_y type="NX_FLOAT">
            {divergence of collimator in local y direction}?
        </divergence_y>
        <frequency type="NX_FLOAT">
            {Frequency of oscillating collimator}?
        </frequency>
        <NXlog name="frequency">
            {Log of frequency}?
        </NXlog>
        <blade_thickness type="NX_FLOAT">
            {}
        </blade_thickness>
        <blade_spacing type="NX_FLOAT">
            {}
        </blade_spacing>
        <absorbing_material type="NX_CHAR">
            {}
        </absorbing_material>
        <transmitting_material type="NX_CHAR">
            {}
        </transmitting_material>
    </NXcollimator>
