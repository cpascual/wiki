---
title: Monochromatic Neutron and X-ray Triple-Axis Spectrometer
permalink: Monochromatic_Neutron_and_X-ray_Triple-Axis_Spectrometer/
layout: wiki
---

    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXmonotas.xml
    Editor:  NIAC
    NIAC Version: 0.1
    $Id: monotas.docbook,v 1.1 2005/06/14 16:50:35 pfp Exp $

    Template of a generic NeXus file containing neutron or x-ray triple-axis data.

    Multianalyzer systems are going to be complicated.  Each analyzer is measuring a
    separate H-K-L-dE.  How this measurement is performed will vary from instrument
    to instrument.  Some will have a different detector for each analyzer.  Others
    will have windows within a 2D detector.  The detector group (which must be
    named "detector") will contain the counts associated with each analyzer.  There 
    may in addition be raw_detector groups which contains the raw detector 
    counts independent of the masks.

    H-K-L-dE are all stored with the sample.  In the multianalyzer case these will
    be arrays with one for each scan point (length np) and one for each analyzer
    (length na).  Note that np must be the first listed dimension.

    Note that the image for each analyzer on the detector could be 0, 1 or 2D,
    depending on whether i,j indices are present.
    -->
    <NXentry name="{Name of entry}">
      <title>
        {Extended title for entry}
      </title>
      <definition URL="http://www.nexus.anl.gov/instruments/xml/NXmonotas.xml"
          version="1.0">
        NXmonotas
      </definition>
      <start_time type="ISO8601">
        {Starting time of measurement}
      </start_time>
      <NXsample name="{name of sample}">
        <name type="NX_CHAR">
          {Descriptive name of sample}?
        </name>
        <unit_cell type="NX_FLOAT32[1,6])">
          {Unit cell parameters (lengths and angles)}?
        </unit_cell>
        <plane_vector_0 type="NX_FLOAT32[3]">
          {Reciprocal space vector of primary reflection in the scattering plane}
        </plane_vector_0>
        <plane_vector_1 type="NX_FLOAT32[3]">
          {Reciprocal space vector of secondary reflection in the scattering plane}
        </plane_vector_1>
        <polar_angle units="degree" type="NX_FLOAT32[np]">
          {Polar angle of the sample with respect to the beam incident on the monochromator}
        </polar_angle>
        <azimuthal_angle units="degree" type="NX_FLOAT32">
          {Azimuthal angle of the sample with respect to the beam incident on the
          monochromator}
        </azimuthal_angle>
        <rotation_angle units="degree" type="NX_FLOAT32[np]">
          {Rotation angle of the sample}
        </rotation_angle>
        <Qh type="NX_FLOAT32[np,na?]">
          {Reciprocal space component of scan}
        </Qh>
        <Qk type="NX_FLOAT32[np,na?]">
          {Reciprocal space component of scan}
        </Qk>
        <Ql type="NX_FLOAT32[np,na?]">
          {Reciprocal space component of scan}
        </Ql>
        <energy_transfer units="meV" type="NX_FLOAT32[np,na?]">
          {Energy transfer of scan}
        </energy_transfer>
      </NXsample>
      <NXinstrument name="{Name of instrument}">
        <NXcollimator name="premonochromator_collimator">
          <type type="NX_CHAR">
            "Soller"|"radial"
          </type>
          <soller_angle units="minute" type="NX_FLOAT32">
            {Angular divergence of Soller collimator}
          </soller_angle>
        </NXcollimator>
        <NXfilter name="premonochromator_filter">
          <description type="NX_CHAR">
            {"Beryllium" | "Pyrolytic Graphite" | "Graphite"}
          </description>
        </NXfilter>
        <NXcrystal name="monochromator">
          <type type="NX_CHAR">
            {"PG (Highly Oriented Pyrolytic Graphite)" | "Ge" | "Si" | "Cu" |
            "Fe3Si" | "CoFe" | "Cu2MnAl (Heusler)" | "Multilayer"}
          </type>
          <energy units="meV" type="NX_FLOAT32[np]">
            {Optimum diffracted energy}
          </energy>
          <d_spacing units="Angstrom" type="NX_FLOAT32">
            {The planar spacing of the nominal reflection}
          </d_spacing>
          <rotation_angle units="degree" type="NX_FLOAT32[np]">
            {Rotation angle of the monochromator}
          </rotation_angle>
          <curvature_horizontal type="NX_FLOAT" units="degrees">?
            {Horizontal curvature of focusing crystal}?
          </curvature_horizontal>
          <curvature_vertical type="NX_FLOAT" units="degrees">?
            {Vertical curvature of focusing crystal}?
          </curvature_vertical>
        </NXcrystal>
        <NXcollimator name="presample_collimator">
          <type type="NX_CHAR">
            "Soller"|"radial"
          </type>
          <soller_angle units="minute" type="NX_FLOAT32">
            {Angular divergence of Soller collimator}
          </soller_angle>
        </NXcollimator>
        <NXfilter name="presample_filter">
          <description type="NX_CHAR">
            {"Beryllium" | "Pyrolytic Graphite" | "Graphite"}
          </description>
        </NXfilter>
        <NXcollimator name="preanalyzer_collimator">
          <type type="NX_CHAR">
            "Soller"|"radial"
          </type>
          <soller_angle units="minute" type="NX_FLOAT32">
            {Angular divergence of Soller collimator}
          </soller_angle>
        </NXcollimator>
        <NXfilter name="preanalyzer_filter">
          <description type="NX_CHAR">
            {"Beryllium" | "Pyrolytic Graphite" | "Graphite"}
          </description>
        </NXfilter>
        <NXcrystal name="analyzer">
          <type type="NX_CHAR">
            {"PG (Highly Oriented Pyrolytic Graphite)" | "Ge" | "Si" | "Cu" |
            "Fe3Si" | "CoFe" | "Cu2MnAl (Heusler)" | "Multilayer"}
          </type>
          <energy units="meV" type="NX_FLOAT32[np,na]">
            {Optimum diffracted energy}
          </energy>
          <d_spacing units="Angstrom" type="NX_FLOAT32">
            {The planar spacing of the nominal reflection}
          </d_spacing>
          <polar_angle units="degree" type="NX_FLOAT32[np,na?]">
            {Polar angle of the analyzer with respect to the beam incident on the
            monochromator}
          </polar_angle>
          <azimuthal_angle units="degree" type="NX_FLOAT32">
            {Azimuthal angle of the analyzer with respect to the beam incident on
            the monochromator}
          </azimuthal_angle>
          <rotation_angle units="degree" type="NX_FLOAT32[np,na?]">
            {Rotation angle of the monochromator}
          </rotation_angle>
          <curvature_horizontal type="NX_FLOAT" units="degrees">?
            {Horizontal curvature of focusing crystal}?
          </curvature_horizontal>
          <curvature_vertical type="NX_FLOAT" units="degrees">?
            {Vertical curvature of focusing crystal}?
          </curvature_vertical>
        </NXcrystal>
        <NXcollimator name="predetector_collimator">
          <type type="NX_CHAR">
            "Soller"|"radial"
          </type>
          <soller_angle units="minute" type="NX_FLOAT32">
            {Angular divergence of Soller collimator}
          </soller_angle>
        </NXcollimator>
        <NXdetector name="detector">
          <counts signal="1" axes="energy_transfer|Qh|Qk|Ql" type="NX_INT32[np,na?,i?,j?]">
            {Integer counts}
          </counts>
          <polar_angle units="degree" type="NX_FLOAT32[np,na?,i?,j?]">
            {Polar angle of the detector with respect to the beam incident on the
            monochromator}
          </polar_angle>
          <azimuthal_angle units="degree" type="NX_FLOAT32[na?,i?,j?]">
            {Azimuthal angle of the detector with respect to the beam incident on
            the analyzer}
          </azimuthal_angle>
          <weight units="dimensionless" type="NX_FLOAT32[np,na?]">?
            {Relative weight of the different analyzers e.g., because the integrated
             regions are not all the same size.}
          </weight>
        </NXdetector>
        <NXdetector name={"raw_detector"}>*
          {Possible set of raw detectors in case the "detector" detector is really
           a virtual detector.}
        </NXdetector>
      </NXinstrument>
      <NXmonitor name="control">
        <mode type="NX_CHAR">
          "monitor"|"timer"
        </mode>
        <preset type="NX_FLOAT32[1]">
          {preset value for time or monitor}
        </preset>
        <data type="NX_INT[np]">
          {Monitor data}?
        </data>
      </NXmonitor>
      <NXdata name="data">
        <Qh NAPIlink="NXentry/NXsample/Qh">
        </Qh>
        <Qk NAPIlink="NXentry/NXsample/Qk">
        </Qk>
        <Ql NAPIlink="NXentry/NXsample/Ql">
        </Ql>
        <energy_transfer NAPIlink="NXentry/NXsample/energy_transfer">
        </energy_transfer>
        <counts NAPIlink="NXentry/NXinstrument/detector/counts">
        </counts>
        <energy NAPIlink="NXentry/NXinstrument/analyzer/energy">
        </energy>
      </NXdata>
    </NXentry>
