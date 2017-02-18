---
title: NXsensor
permalink: NXsensor/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXsensor.xml
    Editor:  NIAC
    $Id: NXsensor.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    This class describes a sensor used to monitor an external condition - the
    condition itself in described in NXenvironment
    -->
    <NXsensor name="{Name of sensor}">
        <model type="NX_CHAR">
            {Sensor identification code/model number}?
        </model>
        <name type="NX_CHAR">
            {Name for the sensor}?
        </name>
        <short_name type="NX_CHAR">
            {Short name of sensor used e.g. on monitor display program}?
        </short_name>
        <attached_to type="NX_CHAR">
            { where sensor is attached to ("sample" | "can") }?
        </attached_to>
        <NXgeometry name="">
            {Defines the axes for logged vector quantities if they are not the 
            global instrument axes}?
        </NXgeometry>
        <measurement type="NX_CHAR">
            { what we measure "temperature | pH | magnetic_field | electric field | 
            conductivity | resistance | voltage | pressure | flow | stress | 
            strain | shear | surface_pressure" }?
        </measurement>
        <type type="NX_CHAR">
            { The type of hardware we use for the measurement e.g. 
            Temperature: "J | K | T | E | R | S | Pt100 | Rh/Fe" 
            pH: "Hg/Hg2Cl2 | Ag/AgCl | ISFET" 
            Ion selective electrode: "specify species; e.g. Ca2+" 
            Magnetic field: "Hall" Surface pressure: "wilhelmy plate" }?
        </type>
        <run_control type="NX_BOOLEAN">
            { Is data collection controlled/synchronised to this quantity: 
            1=no, 0=to "value", 1=to "value_deriv1" etc.}?
        </run_control>
        <high_trip_value type="NX_FLOAT" units="{}">
            {Upper control bound of sensor reading if using run_control}?
        </high_trip_value>
        <low_trip_value type="NX_FLOAT" units="{}">
            {Lower control bound of sensor reading if using run_control}?
        </low_trip_value>
        <value type="NX_FLOAT[n]" units="{}">
            {nominal setpoint or average value - need [n] as may be a vector}?
        </value>
        <value_deriv1 type="NX_FLOAT[n]" units="{}">
            {Nominal/average first derivative of value e.g. strain rate - need [n] 
            as may be a vector}?
        </value_deriv1>
        <value_deriv2 type="NX_FLOAT[n]" units="{}">
            {Nominal/average second derivative of value - need [n] as may be a 
            vector}?
        </value_deriv2>
        <value_log type="NXlog">
            {Time history of sensor readings}?
        </value_log>
        <value_deriv1_log type="NXlog">
            {Time history of sensor readings}?
        </value_deriv1_log>
        <value_deriv2_log type="NXlog">
            {Time history of sensor readings}?
        </value_deriv2_log>
        <external_field_brief type="NX_CHAR">
            { along beam | across beam | transverse | solenoidal | 
            flow shear gradient | flow vorticity }?
        </external_field_brief>
        <external_field_full type="NXorientation">
            {For complex external fields not satisfied by External_field_brief}?
        </external_field_full>
    </NXsensor>
