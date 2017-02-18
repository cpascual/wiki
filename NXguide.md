---
title: NXguide
permalink: NXguide/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXguide.xml
    Editor:  NIAC
    $Id: NXguide.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of NXguide

    -->
    <NXguide name="">
        <NXgeometry name="">
            {}
        </NXgeometry>
        <description type="NX_CHAR">
            {}
        </description>
        <incident_angle type="NX_FLOAT">
            {}
        </incident_angle>
        <reflectivity type="NXdata">
            {Reflectivity as function of wavelength [nsurf,i]}
        </reflectivity>
        <bend_angle_x type="NX_FLOAT">
            {}
        </bend_angle_x>
        <bend_angle_y type="NX_FLOAT">
            {}
        </bend_angle_y>
        <interior_atmosphere type="NX_CHAR">
            "vacuum"|"helium"|"argon"
        </interior_atmosphere>
        <external_material type="NX_CHAR">
            {external material outside substrate}
        </external_material>
        <m_value type="NX_FLOAT[nsurf]">
            {}
        </m_value>
        <substrate_material type="NX_FLOAT[nsurf]">
            {}
        </substrate_material>
        <substrate_thickness type="NX_FLOAT[nsurf]">
            {}
        </substrate_thickness>
        <coating_material type="NX_FLOAT[nsurf]">
            {}
        </coating_material>
        <substrate_roughness type="NX_FLOAT[nsurf]">
            {}
        </substrate_roughness>
        <coating_roughness type="NX_FLOAT[nsurf]">
            {}
        </coating_roughness>
        <number_sections type="NX_INT">
            {number of substrate sections}
        </number_sections>
    </NXguide>
