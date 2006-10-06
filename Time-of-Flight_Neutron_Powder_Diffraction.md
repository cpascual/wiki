---
title: Time-of-Flight Neutron Powder Diffraction
permalink: Time-of-Flight_Neutron_Powder_Diffraction/
layout: wiki
---

Comments
--------

-   Discussion items
    -   time\_focusing\_type (e.g. difc, cubic, ..)
    -   time\_focusing\_parameters \[ndetector,nparameters\]
    -   Definition of groups for binning in NeXus file or via NXdetector
        ?
    -   Deadtime correction information (in combination with gang\_..)
    -   Profile types and starting parameters
    -   Incident spectrum (here in NXcharacterization, alternative
        analytical description ?)

<!-- -->

-   Other
    -   Binned data back in NeXus - this actually is used in Rietveld.

Proposal
--------

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://definitions.nexusformat.org/NXtofnpd.xml
    Editor:  Peter Peterson <petersonpf@sns.gov>
    $Id$

    Instrument definition for a time-of-flight neutron powder diffractometer. 

    -->
    <NXentry name="{Entry Name}">

       <title type="NX_CHAR[]">{Extended title for entry}</title>
       <definition type="NX_CHAR[]" version="$Revision$" URL="definitions.nexusformat.org/NXtofnpd.xml">TOFNPD</definition>
       <start_time type="ISO8601">{Starting time of measurement}</start_time>
       <end_time type="ISO8601">{Ending time of measurement}</end_time>

       <NXinstrument name="{name of the instrument}">
          <name short_name="{abbreviated name of instrument}" type="NX_CHAR[]">{Name of instrument}</name>

          <NXsource name="source">+
             <distance type="NX_FLOAT" units="meter">{distance from the sample (should be negative)}</distance>
          </NXsource>

         <NXdetector name="{Name of detector bank}">
            <time_focusing_type type="NX_CHAR">gsas_difc|gsas_cubic|jason</time_focusing_type>
            <time_focusing_parameters type="NX_FLOAT[fp]">{Parameters for focusing depending on type}</time_focusing_type>

        <time_of_flight type="NX_FLOAT[tof+1]" axis="3" primary="1?" units="microsecond">
            {Total time of flight}+
        </time_of_flight>

        <detector_number type="NX_INT[i?,j?]">
            {Identifier for detector}
        </detector_number>

        <data type="NX_FLOAT[np,i,j,tof]|NX_INT[np,i?,j?,tof?]" signal="1" axes="[number of scan points,x_offset,y_offset,time_of_flight]">
            {Data values}
        </data>

        <data_error type="NX_FLOAT[np?,i?,j?,tof?]|NX_INT[np?,i?,j?,tof?]" units="number">
            {Data values}?
        </data_error>

        <distance type="NX_FLOAT[np?,i?,j?]">
                   {secondary flightpath}
        </distance>

        <polar_angle type="NX_FLOAT[np?,i?,j?]">
                   {polar angle for each detector pixel}
        </polar_angle>

        <azimuthal_angle type="NX_FLOAT[np?,i?,j?]">
                   {azimuthal angle for each detector pixel. If missing, angle assumed to be zero.}?
        </azimuthal_angle>

        <solid_angle type="NX_FLOAT[i?,j?]" units="steradians">
            {Solid angle subtended by the detector at the sample}?
        </solid_angle>

        <dead_time type="NX_FLOAT[np?,i?,j?]">
            {Detector dead time}?
        </dead_time>

            <layout type="NX_CHAR">point|linear|area{How the detector is represented}</layout>
          </NXdetector>
     
          <NXcharacterization name="isotropic_scatterer" NXS:source="{If missing the source file is the
              current file}?" NXS:location="" NXS:mime_type="{If missing the source file is NAPI readable}">
          <definition version="$Revision$" URL="definitions.nexusformat.org/NXtofnpd.xml">TOFNPD</definition>
          </NXcharacterization>

         <NXcharacterization name="isotropic_scatterer_background" NXS:source="{If missing the source file is the
              current file}?" NXS:location="" NXS:mime_type="{If missing the source file is NAPI readable}?">
          <definition version="$Revision$" URL="definitions.nexusformat.org/NXtofnpd.xml">TOFNPD</definition>
          </NXcharacterization>

        <NXcharacterization name="empty_environment" NXS:source="{If missing the source file is the
              current file}?" NXS:location="" NXS:mime_type="{If missing the source file is NAPI readable}?">
          <definition version="$Revision$" URL="definitions.nexusformat.org/NXtofnpd.xml">TOFNPD</definition>
          </NXcharacterization>
       </NXinstrument>

       <NXmonitor name="{name of the monitor}">*
          <distance type="NX_FLOAT" units="meter"></distance>
          <time_of_flight type="NX_FLOAT[i]|NX_INT[i]" units="microsecond"></time_of_flight>
          <data type="NX_FLOAT[i]|NX_INT[i]" units="number"></data>
          <data_error type="NX_FLOAT[i]|NX_INT[i]" units="number">?</data_error>
       </NXmonitor>

       <NXdata name="">+
          <time_of_flight>{Link to time_of_flight in NXdetector}</time_of_flight>
          <detector_number>{Link to detector_number in NXdetector}</detector_number>
          <data>{Link to data in NXdetector}</data>
       </NXdata>

    </NXentry>