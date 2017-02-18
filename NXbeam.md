---
title: NXbeam
permalink: NXbeam/
layout: wiki
---

    <?xml version="1.0" encoding="UTF-8"?>
    <!--
    URL:     http://www.nexus.anl.gov/classes/xml/NXbeam.xml
    Editor:  NIAC
    $Id: NXbeam.xml,v 1.2 2005/07/19 04:10:26 rio Exp $

    Template of the state of the neutron or X-ray beam at any location. It will be
    referenced by beamline component groups within the NXinstrument group or by the
    NXsample group. Note that variables such as the incident energy could be scalar
    values or arrays. This group is especially valuable in storing the results of
    instrument simulations in which it is useful to specify the beam profile, time
    distribution etc. at each beamline component. Otherwise, its most likely use is
    in the NXsample group in which it defines the results of the neutron scattering
    by the sample, e.g., energy transfer, polarizations.

    -->
    <NXbeam name="{Name of beam plane}">
        <distance type="NX_FLOAT" units="m">
            {Distance from sample}?
        </distance>
        <incident_energy type="NX_FLOAT[:]" units="meV">
            {Energy on entering beamline component}?
        </incident_energy>
        <final_energy type="NX_FLOAT[:]" units="meV">
            {Energy on leaving beamline component}?
        </final_energy>
        <energy_transfer type="NX_FLOAT[:]" units="meV">
            {Energy change caused by beamline component }?
        </energy_transfer>
        <incident_wavelength type="NX_FLOAT[:]" units="Angstroms">
            {Wavelength on entering beamline component}?
        </incident_wavelength>
        <incident_wavelength_spread type="NX_FLOAT[:]" units="Angstroms">
            {Wavelength spread FWHM on entering component}?
        </incident_wavelength_spread>
        <incident_beam_divergence type="NX_FLOAT[2,:]" units="degree">
            {Divergence of beam entering this component}?
        </incident_beam_divergence>
        <final_wavelength type="NX_FLOAT[:]">
            {Wavelength on leaving beamline component}?
        </final_wavelength>
        <incident_polarization type="NX_FLOAT[3,:]">
            {Polarization vector on entering beamline component}?
        </incident_polarization>
        <final_polarization type="NX_FLOAT[3,:]">
            {Polarization vector on leaving beamline component}?
        </final_polarization>
        <final_wavelength_spread type="NX_FLOAT[:]" units="Angstroms">
            {Wavelength spread FWHM of beam leaving this component}?
        </final_wavelength_spread>
        <final_beam_divergence type="NX_FLOAT[2,:]" units="degrees">
            {Divergence FWHM of beam leaving this component}?
        </final_beam_divergence>
        <flux type="NX_FLOAT[i]" units="s-1cm-2">
            {flux incident on beam plane area}?
        </flux>
        <NXdata name="{spectrum}">
            {Distribution of beam with respect to relevant variable e.g. wavelength. 
            This is mainly useful for simulations which need to store plottable 
            information at each beamline component. }?
        </NXdata>
    </NXbeam>
