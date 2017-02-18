---
title: NXmonitor
permalink: NXmonitor/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXmonitor.xml
    Editor:  NIAC
    $Id: NXmonitor.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of monitor data. It is similar to the NXdata groups containing
    monitor data and its associated dimension scale, e.g. time_of_flight or
    wavelength in pulsed neutron instruments. However, it may also include
    integrals, or scalar monitor counts, which are often used in both in both
    pulsed
    and steady-state instrumentation.

    -->
    <NXmonitor name="{Name of monitor}">
        <mode type="NX_CHAR">
            "monitor"|"timer"?
        </mode>
        <preset type="NX_FLOAT">
            {preset value for time or monitor}?
        </preset>
        <distance type="NX_FLOAT" units="m">
            {Distance of monitor from sample}?
        </distance>
        <range type="NX_FLOAT[2]">
            {Time-of-flight range over which the integral was calculated}?
        </range>
        <integral type="NX_FLOAT" units="">
            {Total integral monitor counts}?
        </integral>
        <integral_log type="NXlog" units="">
            {Time variation of monitor counts}?
        </integral_log>
        <type type="NX_CHAR">
            "Fission Chamber"|"Scintillator"?
        </type>
        <time_of_flight type="NX_FLOAT[i]" units="microseconds">
            {Time-of-flight}?
        </time_of_flight>
        <efficiency type="NX_FLOAT[i]">
            {Monitor efficiency}?
        </efficiency>
        <data type="NX_INT[i]" units="" signal="1" axes="">
            {Monitor data}?
        </data>
        <sampled_fraction type="NX_FLOAT" units="dimensionless">
            {Proportion of incident beam sampled by the monitor (0&lt;x&lt;1)}
        </sampled_fraction>
        <NXgeometry name="">
            {Geometry of the monitor}?
        </NXgeometry>
    </NXmonitor>
