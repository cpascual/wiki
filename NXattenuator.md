---
title: NXattenuator
permalink: NXattenuator/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXaperture.xml
    Editor:  NIAC
    $Id: NXattenuator.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of a beamline attenuator.

    -->
    <NXattenuator name="{Name of attenuator}">
        <distance type="NX_FLOAT" units="m">
            {Distance from sample}?
        </distance>
        <type type="NX_CHAR">
            {Type of attenuator, e.g. polythene}?
        </type>
        <thickness type="NX_FLOAT" units="cm">
            {Thickness of attenuator along beam direction}?
        </thickness>
        <scattering_cross_section type="NX_FLOAT" units="barns">
            {Scattering cross section (coherent+incoherent)}?
        </scattering_cross_section>
        <absorption_cross_section type="NX_FLOAT" units="barns">
            {Absorption cross section}?
        </absorption_cross_section>
        <attenuator_transmission type="NX_FLOAT">
            {The nominal amount of the beam that gets through 
            (transmitted intensity)/(incident intensity)}?
        </attenuator_transmission>
    </NXattenuator>
