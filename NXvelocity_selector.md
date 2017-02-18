---
title: NXvelocity selector
permalink: NXvelocity_selector/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXvelocity_selector.xml
    Editor:  Ron Ghosh
    $Id: NXvelocity_selector.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    This is the description for a velocity selector.
    Proposed by: Ron Ghosh

    -->
    <NXvelocity_selector name="selector_name">
        <type type="NX_CHAR">
            {Vselect type}? 
        </type>
        <rotation_speed type="NX_FLOAT" units="rpm">
            {selector rotation speed}? 
        </rotation_speed>
        <radius type="NX_FLOAT" units="cm">
            {radieus at beam centre}? 
        </radius>
        <spwidth type="NX_FLOAT" units="cm">
            {spoke width at beam centre}? 
        </spwidth>
        <length type="NX_FLOAT" units="cm">
            {rotor length}? 
        </length>
        <num type="NX_INT">
            {number of spokes/lamella}? 
        </num>
        <twist type="NX_FLOAT" units="degrees">
            {twist angle along axis}? 
        </twist>
        <table type="NX_FLOAT" units="degrees">
            {offset vertical angle}? 
        </table>
        <height type="NX_FLOAT" units="cm">
            {input beam height}? 
        </height>
        <width type="NX_FLOAT" units="cm">
            {input beam width}? 
        </width>
        <wavelength type="NX_FLOAT" units="nm">
            {wavelength} 
        </wavelength>
        <wavelength_spread type="NX_FLOAT">
            {% deviation FWHM /Wavelength}? 
        </wavelength_spread>
        <NXgeometry name="">
            {geometry of the velocity selector}? 
        </NXgeometry>
    </NXvelocity_selector>
