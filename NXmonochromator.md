---
title: NXmonochromator
permalink: NXmonochromator/
layout: wiki
---

This is a base class for everything which selects a wavelength or
energy, be it a monochromator crystal, a velocity selector, a undulator
or whatever.

    <NXmonochromator name="name of monochromator">
      <!--
        expected units
        wavelength: angstrom
        energy:     eV
      -->
      <wavelength type="NX_FLOAT[]" units="{unit}">
         {wavelength selected}
      </wavelength> 
      <wavelength_error type="NX_FLOAT[]" units="{unit}">
         {wavelength standard deviation}
      </wavelength_error> 
      <energy type="NX_FLOAT[]" units="{unit}">
         {energy selected}
      </energy > 
      <energy_error type="NX_FLOAT[]" units="{unit}">
         {energy standard deviation}
      </energy_error> 
      <NXdata name="distribution"/> 
    </NXmonochromator>
