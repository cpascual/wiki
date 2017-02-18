---
title: NXsample
permalink: NXsample/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXsample.xml
    Editor:  NIAC
    $Id: NXsample.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of the state of the sample. This could include scanned variables that
    are associated with one of the data dimensions, e.g. the magnetic field, or
    logged data, e.g. monitored temperature vs elapsed time.

    -->
    <NXsample name="{name of the sample}">
        <name type="NX_CHAR">
            {Descriptive name of sample}?
        </name>
        <chemical_formula type="NX_CHAR">
            {The chemical formula specified using CIF conventions.}{Abbreviated
            version of CIF standard: 1. Only recognized element symbols may be used.
            2. Each element symbol is followed by a 'count' number. A count of '1'
            may be omitted. 3. A space or parenthesis must separate each cluster of
            (element symbol + count). 4. Where a group of elements is enclosed in
            parentheses, the multiplier for the group must follow the closing
            parentheses. That is, all element and group multipliers are assumed to
            be printed as subscripted numbers. 5. Unless the elements are ordered in
            a manner that corresponds to their chemical structure, the order of the
            elements within any group or moiety depends on whether or not carbon is
            present. If carbon is present, the order should be: C, then H, then the
            other elements in alphabetical order of their symbol. If carbon is not
            present, the elements are listed purely in alphabetic order of their
            symbol. This is the 'Hill' system used by Chemical Abstracts.}?
        </chemical_formula>
        <temperature type="NX_FLOAT[:]">
            {Sample temperature. This could be a scanned variable}?
        </temperature>
        <electric_field type="NX_FLOAT[:]" direction="x|y|z">
            {Applied electric field}*
        </electric_field>
        <magnetic_field type="NX_FLOAT[:]" direction="x|y|z">
            {Applied magnetic field}*
        </magnetic_field>
        <stress_field type="NX_FLOAT[:]" direction="x|y|z">
            {External stress}*
        </stress_field>
        <pressure type="NX_FLOAT[:]">
            {Applied pressure}?
        </pressure>
        <changer_position type="NX_INT">
            {Sample changer position}?
        </changer_position>
        <unit_cell type="NX_FLOAT[n_comp,6])">
            {Unit cell parameters (lengths and angles)}?
        </unit_cell>
        <unit_cell_volume type="NX_FLOAT[n_comp]" units="Angstroms3" rank="1">
            {Volume of the unit cell}?
        </unit_cell_volume>
        <sample_orientation type="NX_FLOAT[3]" units="degree">
            {This will follow the Busing and Levy convention from Acta.Crysta v22, 
            p457 (1967)}?
        </sample_orientation>
        <orientation_matrix type="NX_FLOAT[n_comp,3,3]">
            {Orientation matrix of single crystal sample}{The is the orientation 
            matrix using Busing-Levy convention}?
        </orientation_matrix>
        <mass type="NX_FLOAT[n_comp]" units="g">
            {Mass of sample}?
        </mass>
        <density type="NX_FLOAT[n_comp]" units="g cm-3">
            {Density of sample}?
        </density>
        <relative_molecular_mass type="NX_FLOAT[n_comp]">
            {Relative Molecular Mass of sample}?
        </relative_molecular_mass>
        <type type="NX_CHAR">
            { sample | sample+can | can | calibration sample | normalisation sample | simulated data | none | sample environment }?
        </type>
        <situation type="NX_CHAR">
            { air | vacuum | inert atmosphere | oxidising atmosphere | 
            reducing atmosphere | sealed can | other }
            {The atmosphere will be one of the components, which is where its 
            details will be stored; the relevant components will be indicated by the 
            entry in the sample_component member.}?
        </situation>
        <description type="NX_CHAR">
            {Description of the sample}?
        </description>
        <preparation_date type="ISO8601">
            {Date of preparation of the sample}?
        </preparation_date>
        <geometry type="NXgeometry">
            {The position and orientation of the center of mass of the sample}?
        </geometry>
        <beam type="NXbeam">
            {Details of beam incident on sample - used to calculate sample/beam 
            interaction point}?
        </beam>
        <component type="NX_CHAR[n_comp]">
            {Details of the component of the sample and/or can}?
        </component>
        <sample_component type="NX_CHAR[n_comp]">
            { What type of component we are "sample | can | atmosphere | kit" }?
        </sample_component>
        <concentration type="NX_FLOAT[n_comp]" units="g.cm-3">
            {Concentration of each component}?
        </concentration>
        <volume_fraction type="NX_FLOAT[n_comp]">
            {Volume fraction of each component}?
        </volume_fraction>
        <scattering_length_density type="NX_FLOAT[n_comp]">
            {Scattering length density of each component (cm-2)}?
        </scattering_length_density>
        <unit_cell_class type="NX_CHAR[n_comp]">
            { In case it is all we know and we want to record it "cubic | 
            tetragonal | orthorhombic | monoclinic | triclinic" }?
        </unit_cell_class>
        <unit_cell_group type="NX_CHAR[n_comp]">
            {Crystallographic point or space group}?
        </unit_cell_group>
        <path_length type="NX_FLOAT">
            {Path length through sample/can for simple case when it does not vary 
            with scattering direction}?
        </path_length>
        <path_length_window type="NX_FLOAT">
            {Thickness of a beam entry/exit window on the can (mm) - assumed same 
            for entry and exit}?
        </path_length_window>
        <transmission type="NXdata">
            {As a function of Wavelength}?
        </transmission>
        <temperature_log type="NXlog">
            {temperature_log.value is a link to e.g. 
            temperature_env.sensor1.value_log.value}?
        </temperature_log>
        <temperature_env type="NXenvironment">
            {Additional sample environment information}?
        </temperature_env>
        <magnetic_field_log type="NXlog">
            {magnetic_field_log.value is a link to e.g. 
            magnetic_field_env.sensor1.value_log.value}?
        </magnetic_field_log>
        <magnetic_field_env type="NXenvironment">
            {Additional sample environment information}?
        </magnetic_field_env>
        <external_DAC type="NX_FLOAT">
            {value sent to user's sample setup}?
        </external_DAC>
        <external_ADC type="NXlog">
            {logged value (or logic state) read from user's setup}?
        </external_ADC>
        <short_title type="NX_CHAR">
            {20 character fixed length sample description for legends}?
        </short_title>
    </NXsample>
