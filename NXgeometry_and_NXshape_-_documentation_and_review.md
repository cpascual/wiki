---
title: NXgeometry and NXshape - documentation and review
permalink: NXgeometry_and_NXshape_-_documentation_and_review/
layout: wiki
---

NXgeometry
----------

![ upright | frame | right | c | UML diagramm of the relations between
the different geometry related base classes.
](Nxgeometry_uml.png "fig: upright | frame | right | c | UML diagramm of the relations between the different geometry related base classes. ")
Geometries in Nexus are described using the *NXgeometry* base class. As
shown in the UML diagramm on the right side this class consists
basically of three other base classes (composition): *NXshape*,
*NXtranslation*, and *NXorientation*. As far as I understand the
*NXgeometry* class it describes a single shape (geometric object). This
fact makes the dimensionality of several attributes of the the other
classes a bit odd (see below). However, aside from this *NXgeometry* is
quite ok.

NXtranslation
-------------

Has an attribute *distances* of shape `[numobj,3]`. If, as stated above,
*NXgeometry* seems to describe only a single shape the first dimension
has no meaning. A dimensionality of `[3]` would be enough for this
field.

NXorientation
-------------

Has an attribute *value* of shape `[numobj,6]`. If, as stated above,
*NXgeometry* seems to describe only a single shape the first dimension
has no meaning. A dimensionality of `[6]` would be enough for this
field.

NXshape
-------

This is where all the problems start. In fact there are three issues
with this class

-   as for *NXtranslation* and *NXorientation* the first dimension of
    the *size* attribute (`numobj`) has no meaning
-   what is the attribute *direction* good for (its values *convex* and
    *concav* are not defined)
-   last but not least: the shapes are not defined well (this is the
    major issue)

The last problem will be discussed in more detail in the following
sections.

### Definition of geometric primitives

Every geometric primitive requires a local coordinate frame. All
translations applied on a primitive will act on the origin of this local
frame. Additionally, the origin of this frame of reference will act as a
center for all rotations applied on the primitive. Unfortunately, the 9
geometric primitives currently availbable in Nexus are not defined in
such a sens. The following sections provide some possible definitions of
these primitives along with the layout of their parameters stored in the
*size* attribute of *NXshape*.

<File:nxflat_image.png> | Shape and coordinate frame for an *nxflat*
<File:Nxcylinder.png> | An *nxcylinder* in its local frame
<File:Nxbox_image.png> | An *nxbox* in its local frame

#### nxflat

*nxflag* can be considered as a flat plane. The plane defines the
x-y-plane of its local coordinate frame. The z-axis of this system is
oriented so that the resulting reference frame is a right-handed one.
The shape has two parameters: its *height* and *width* which will be
stored in the *size* attribute of *NXshape* as follows

`NXshape::size[2]={width,height}`

#### nxcylinder

The origin of the local coordinate frame for *nxcylinder* is in the
center of its bottom. An *nxcylinder* has 5 parameters: radius, height,
and the three components of the direction vector v (see the figure
above). These parameters are stored in the *size*attribute of *NXshape*
as follows

`NXshape::size[5] = {radius,height,vx,vy,vz}`

#### nxbox

`NXshape::size[3] = {length,width,height}`

<File:nxsphere_image.png> | Shape and coordinate frame for an *nxsphere*

#### nxsphere

`NXshape::size[1] = {radius}`

#### nxcone

#### nxelliptical

#### nxtoroidal

#### nxparabolic

#### nxpolynomial