---
title: NXtranslation
permalink: NXtranslation/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXtranslation.xml
    Editor:  NIAC
    $Id: NXtranslation.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    This is the description for the general spatial location
    of a component - it is used by the NXgeometry.xml class
    -->
    <NXtranslation name="{name of translation}">
        <NXgeometry name="{geometry}">
            {Link to other object if we are relative , else absent}?
        </NXgeometry>
        <distances type="NX_FLOAT[numobj,3]" units="">
            {(x,y,z)}{This field and the angle field describe the position of a
            component. For absolute position, the origin is the scattering center
            (where a perfectly aligned sample would be) with the z-axis pointing
            downstream and the y-axis pointing gravitationally up. For a relative
            position the NXtranslation is taken into account before the
            NXorientation. The axes are right-handed and orthonormal.}?
        </distances>
    </NXtranslation>
