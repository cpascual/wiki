---
title: NeXpy
permalink: NeXpy/
layout: wiki
---

NeXpy provides a high-level python interface to NeXus data contained
within a simple GUI. It is designed to provide an intuitive interactive
toolbox allowing users both to access existing NeXus files and to create
new NeXus-conforming data structures without expert knowledge of the
file format.

Installation
------------

WARNING: NeXpy is in the early stages of development, and so there has
been no stable release yet. It is available for testing purposes only.

To check out the latest version from the
[Mercurial](http://mercurial.selenic.com/) repository and install the
NeXpy package to the standard python site-packages directory,:

`> hg clone `[`http://mercurial.mcs.anl.gov/repos/nexpy`](http://mercurial.mcs.anl.gov/repos/nexpy)  
`> cd nexpy`  
`> python setup.py install`  
` `

This assumes that the standard Python script directory is in your
default path.

The source code can also be viewed on the [NeXpy Trac
Server](http://trac.mcs.anl.gov/projects/nexpy/).

### Installation Issues

#### Locating the NeXus library

NeXpy utilizes the python wrapper to the NeXus C API distributed with
the standard NeXus distribution. This wrapper needs the location of the
libNeXus precompiled binary. It looks in the following places in order::

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Location</p></th>
<th><p>Operating System</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>os.environ['NEXUSLIB']</p></td>
<td><p>All</p></td>
</tr>
<tr class="even">
<td><p>directory containing napi.py</p></td>
<td><p>All</p></td>
</tr>
<tr class="odd">
<td><p>os.environ['NEXUSDIR']\bin</p></td>
<td><p>Windows</p></td>
</tr>
<tr class="even">
<td><p>os.environ['LD_LIBRARY_PATH']</p></td>
<td><p>Unix</p></td>
</tr>
<tr class="odd">
<td><p>os.environ['DYLD_LIBRARY_PATH']</p></td>
<td><p>Darwin</p></td>
</tr>
<tr class="even">
<td><p>PREFIX/lib</p></td>
<td><p>Unix and Darwin</p></td>
</tr>
<tr class="odd">
<td><p>/usr/local/lib</p></td>
<td><p>Unix and Darwin</p></td>
</tr>
<tr class="even">
<td><p>/usr/lib</p></td>
<td><p>Unix and Darwin</p></td>
</tr>
<tr class="odd">
</tr>
</tbody>
</table>

-   On Windows it looks for one of libNeXus.dll or libNeXus-0.dll.
-   On OS X it looks for libNeXus.dylib
-   On Unix it looks for libNeXus.so

NEXUSDIR defaults to r'C:\\Program Files\\NeXus Data Format'. PREFIX
defaults to /usr/local, but is replaced by the value of --prefix during
configure.

The import will raise an OSError exception if the library wasn't found
or couldn't be loaded. Note that on Windows in particular this may be
because the supporting HDF5 dlls were not available in the usual places.

If you are extracting the nexus library from a bundle at runtime, set
os.environ\['NEXUSLIB'\] to the path where it is extracted before the
first import of nexpy.

#### wxPython Installation

Some prepackaged rpms do not install wxgtk with all features enabled. In
particular, the NeXpy GUI may require that wxgtk be built from source
with the '--enable-graphics\_ctx' configure option

Running NeXpy
-------------

There are two ways of using the NeXpy interface to NeXus files.

1.  Within a standard python or ipython shell.
2.  Using the GUI shell

### Python Shell

`$ python`  
`Python 2.5.4`  
`[GCC 4.0.1 (Apple Computer, Inc.)] on darwin`  
`Type `“`help`”`, `“`copyright`”`, `“`credits`”` or `“`license`”` for more information.`  
`>>> from nexpy.api import nexus`  
`>>> a=nexus.load('data/chopper.nxs')`

### GUI Shell

To run the NeXpy GUI, type

`> nexpy`

![NeXpy|center|800px](Nexpy.png "fig:NeXpy|center|800px") The GUI
contains three main panes:

Tree Pane:This contains the tree structure of NeXus files opened in the File menu and/or any NXroot and NXentry groups created within the shell.  
Plot Pane:Any NXdata or NXmonitor group can be plotted in this pane by right-clicking on the relevant node in the tree.  
Shell Pane:This is a regular python shell, with both Numpy and NeXpy already imported (as \* so no prefixes are necessary). Any assignments to items in the tree pane are automatically reflected in the tree pane, and new NXroot, NXentry, or NXdata objects are added to the tree. Currently, it is not possible to plot directly from the shell pane, but this will be added in the future.  

There are a number of useful features available when running NeXpy
within the GUI shell.

1.  Data can be loaded with the <File:Open> menu item using a standard
    file browser window.
2.  All current NeXus data trees are easy to inspect in the pane on the
    upper left side. Hovering over a data item produces a tooltip
    containing a list of all the item's children.
3.  The root level of all newly created groups are automatically
    displayed in the tree.
4.  Any changes to data sets in the scripting window will be reflected
    within the tree pane, including the creation of new NXroot or
    NXentry groups.
5.  NXdata and NXmonitor plots can be displayed by right-clicking and
    choosing 'Plot'.
6.  Axis limits are set by a series of slider bars.
7.  The scripting shell provides convenient autocompletion, and
    automatically displays function docstrings as a tooltip when you
    open the function parentheses.

#### Planned Enhancements

-   Plotting projections along any axis by dragging and right-clicking
    the plots.
-   Editing data items in the tree within an editor pane.
-   Fitting data with predefined and user-supplied functions.

NeXus Interface
---------------

### Loading NeXus Data

The entire tree structure of a NeXus file can be loaded by a single
command.

`>>> from nexpy.api import nexus`  
`>>> a=nexus.load('sns/data/ARCS_7326_tof.nxs')`

The assigned variable now contains the entire tree structure of the
file, which can be displayed with the nxtree() method.

`>>> a.nxtree()`  
`root:NXroot`  
` @HDF5_Version = 1.8.2`  
` @NeXus_version = 4.2.1`  
` @file_name = ARCS_7326_tof.nxs`  
` @file_time = 2010-05-05T01:59:25-05:00`  
` entry:NXentry`  
`   `[`data:NXdata`](data:NXdata)  
`     data = float32(631x461x4x825)`  
`       @axes = rotation_angle:tilt_angle:sample_angle:time_of_flight`  
`       @signal = 1`  
`     rotation_angle = float32(632)`  
`       @units = degree`  
`     sample_angle = [ 210.  215.  220.  225.  230.]`  
`       @units = degree`  
`     tilt_angle = float32(462)`  
`       @units = degree`  
`     time_of_flight = float32(826)`  
`       @units = microsecond`  
`   run_number = 7326`  
`   sample:NXsample`  
`     pulse_time = 2854.94747365`  
`       @units = microsecond`

Individual data items are immediately available from the command-line.

`>>> print a.entry.run_number`  
`7326`

Note that only the tree structure and smaller data sets are read into
memory to avoid using up memory unnecessarily. In the above example,
only the types and dimensions of the larger data sets are displayed in
the tree. However, the filename is also stored, so the data can be
loaded as soon as it is needed, either as a complete array or as a
series of slabs.

### Creating NeXus Data

It is just as easy to create new NeXus data sets from scratch using
Numpy arrays. The following example shows the creation of a simple
function, which is then saved to a file.

`>>> import numpy as np`  
`>>> x=y=np.linspace(0,2*np.pi,101)`  
`>>> X,Y=np.meshgrid(x,y)`  
`>>> z=np.sin(X)*np.sin(Y)`  
`>>> a=NXdata(z,[x,y])`  
`>>> a.nxsave('function.nxs')`

This file can then be loaded again.

`>>> b=nexus.load('function.nxs')`  
`>>> b.nxtree()`  
`root:NXroot`  
` @HDF5_Version = 1.8.2`  
` @NeXus_version = 4.2.1`  
` @file_name = function.nxs`  
` @file_time = 2010-05-10T17:01:13+01:00`  
` entry:NXentry`  
`   `[`data:NXdata`](data:NXdata)  
`     axis1 = float64(101)`  
`     axis2 = float64(101)`  
`     signal = float64(101x101)`  
`       @axes = axis1:axis2`  
`       @signal = 1`

Note that the nxsave() method automatically wraps any valid NeXus data
in an NXentry group, in order to produce a standard-compliant file.

#### Scientific Data Sets (SDS)

NeXus data values are stored in NeXus objects of class 'SDS'. The SDS
class wraps standard Numpy arrays, scalars, and python strings so that
data attributes can be associated with them. There are two ways to
create an SDS.

-   Explicit initialization. The data value is given by the first
    positional argument, and may be a python scalar or string, or a
    Numpy array. In this method, keyword arguments can be used to define
    SDS attributes.

`>>> x = SDS(np.linspace(0,2*np.pi,101), units='degree')`

-   Implicit initialization as the child of a NeXus group. The assigned
    values are automatically converted to an SDS.

`>>> a.entry.sample.temperature=40.0`  
`>>> a.entry.sample.temperature`  
`SDS(name=temperature,value=40.0)`

SDS attributes can be assigned after creating the SDS. Note that
attribute names must not start with 'nx' to avoid name clashes.

`>>> a.entry.sample.temperature.units='K'`

The actual values of an SDS are stored in the 'nxdata' attribute. If the
SDS is read in from a data file, this attribute is not input if the
array size is large to avoid using up memory unnecessarily. It will,
however, be read in if the value is accessed for plotting or
manipulating data. If this will cause a memory exception, the data
should be read in as a series of slabs using the nxget method.

`>>> with root.NXentry[0].data.data as slab:`  
`              Ni,Nj,Nk = slab.nxdims`  
`               size = [1,1,Nk]`  
`               for i in range(Ni):`  
`                   for j in range(Nj):`  
`                       value = slab.nxget([i,j,0],size)`

Data values can be returned converted to different units if the 'units'
attribute has been set.

`>>> phi = x.nxdata_as(units='radian')`  
`>>> y = SDS(np.sin(phi))`

#### NeXus Groups

NeXus groups are defined as subclasses of the NXgroup class. Apart from
the class name, they behave identically except for the NXdata,
NXmonitor, and NXlog groups, which have extra methods defined. The
initialization parameters can be used to populate the group with other
predefined NeXus objects, either groups or SDSs.

`>>> temperature = SDS(40.0, units='K')`  
`>>> sample = NXsample(temperature=temperature)`  
`>>> sample.nxtree()`  
`sample:NXsample`  
`  temperature = 40.0`  
`  units = K`

Note that, in this example, it was necessary to use the keyword form to
add the SDS 'temperature' since its name is otherwise undefined within
the NXsample group. This name is set automatically if the SDS is added
as an attribute assignment.

`>>> sample = NXsample()`  
`>>> sample.temperature=SDS(40.0, units='K')`  
`sample:NXsample`  
`  temperature = 40.0`  
`  units = K`

NXdata Groups  
NXdata groups contain data ready to be plotted. That means that the
group should consist of an SDS containing the data and one or more SDSs
containing the axes. NeXus defines a method of associating axes with the
appropriate dimension, but NeXpy provides a simple constructor that
implements this method automatically.

This was already demonstrated in the example above, reproduced here:

`>>> import numpy as np`  
`>>> x=y=np.linspace(0,2*np.pi,101)`  
`>>> X,Y=np.meshgrid(x,y)`  
`>>> z=np.sin(X)*np.sin(Y)`  
`>>> a=NXdata(z,[x,y])`

  
The first positional argument is an SDS or Numpy array containing the
data, while the second is a list containing the axes, again as SDSs or
Numpy arrays. In this example, the names of the arrays have not been
defined within an SDS so default names were assigned.

`>>> a.nxtree()`  
`   `[`data:NXdata`](data:NXdata)  
`     axis1 = float64(101)`  
`     axis2 = float64(101)`  
`     signal = float64(101x101)`  
`       @axes = axis1:axis2`  
`       @signal = 1`

  
However, names can be assigned explicitly when creating the SDS through
the 'name' attribute.

`>>> phi=np.linspace(0,2*np.pi,101)`  
`>>> data=np.sin(phi)`  
`>>> a=NXdata(SDS(data,name='intensity'),(SDS(phi,name='polar_angle')))`  
`>>> a.nxtree()`  
[`data:NXdata`](data:NXdata)  
`  intensity = float64(101)`  
`    @axes = polar_angle`  
`    @signal = 1`  
`  polar_angle = float64(101)`

### Plotting NeXus Data

#### Python Shell

NXdata, NXmonitor, and NXlog groups all have a nxplot method, which
automatically determines what should be plotted.

`>>> data.nxplot()`

![A simple NeXpy
plot|center](NeXPy-Simple_plot.png "fig:A simple NeXpy plot|center") If
the data is one-dimensional, it is possible to overplot more than one
data set using 'over=True'. Conventional Matplotlib keywords can be used
to change markers and colors.

`>>> data.nxplot(log=True)`  
`>>> data.nxplot(over=True, log=True, color='r')`

#### GUI Shell

NXdata, NXmonitor, and NXlog data can be plotted by right-clicking on
the group within the tree. The plot pane contains a toolbar to change
axis or signal intensity limits. The slider provides a graphical way of
setting minimum and/or maximum values or they can be typed into the text
boxes. ![Axis Limits
Toolbar|center|600px](Axis_Limits_Bar.png "fig:Axis Limits Toolbar|center|600px")
There are two checkboxes:

Lock:If the maximum and/or minimum values are not set to the limits, then this checkbox locks the difference between the two. The arrows can be used to step with this width through the entire range.  
Collapse:The two limits are collapsed onto a single value. This is particularly useful for stepping one slice at a time through the orthogonal direction for three- or higher-dimensional data.  

### Manipulating NeXus Data

### Slicing

#### SDS

A slice of an SDS can be obtained using the usual python indexing
syntax.

`>>> x=SDS(np.linspace(0,2*np.pi,101))`  
`>>> print x[0:51]`  
`[ 0.          0.06283185  0.12566371 ...,  3.01592895  3.0787608 3.14159265]`

If either of the indices are floats, then the limits are set by the
values themselves (assuming the array is monotonic).

`>>> print x[0.5:1.5]`  
`[ 0.50265482  0.56548668  0.62831853 ...,  1.38230077  1.44513262 1.50796447]`

#### NXdata

It is also possible to slice whole NXdata groups. In this case, the
slicing works on the multidimensional SDS, but the full NXdata group is
returned with both the signal data and the associated axes limited by
the slice parameters. If either of the limits along any one axis is a
float, the limits are set by the values of the axis.

`>>> a=NXdata(np.sin(x),x)`  
`>>> a[1.5:2.5].x`  
`SDS(name=x,value=[ 1.57079633  1.72787596  1.88495559 ...,  2.19911486  2.35619449])`

Unless the slice reduces one of the axes to a single item, the rank of
the data remains the same. To project data along one of the axes, and so
reduce the rank by one, the data can be summed along that axis using the
nxsum() method. This employs the Numpy array sum() method.

`>>> x=y=SDS(np.linspace(0,2*np.pi,41))`  
`>>> X,Y=np.meshgrid(x,y)`  
`>>> a=NXdata(np.sin(X)*np.sin(Y), (x,y))`  
`>>> a.nxtree()`  
[`data:NXdata`](data:NXdata)  
`  axis1 = float64(41)`  
`  axis2 = float64(41)`  
`  signal = float64(41x41)`  
`    @axes = axis1:axis2`  
`    @signal = 1`  
`>>> a.nxsum(0).nxtree()`  
[`data:NXdata`](data:NXdata)  
`  axis2 = float64(41)`  
`  signal = float64(41)`  
`    @axes = axis2`  
`    @long_name = Integral from 0.0 to 6.28318530718 `  
`    @signal = 1`

It is also possible to slice whole NXdata groups. In this case, the
slicing works on the multidimensional SDS, but the full NXdata group is
returned with both the signal data and the associated axes limited by
the slice parameters. If either of the limits along any one axis is a
float, the limits are set by the values of the axis.

`>>> a=NXdata(np.sin(x),x)`  
`>>> a[1.5:2.5].x`  
`SDS(name=x,value=[ 1.57079633  1.72787596  1.88495559 ...,  2.19911486  2.35619449])`

Unless the slice reduces one of the axes to a single item, the rank of
the data remains the same. To project data along one of the axes, and so
reduce the rank by one, the data can be summed along that axis using the
nxsum() method. This employs the Numpy array sum() method.

`>>> x=y=SDS(np.linspace(0,2*np.pi,41))`  
`>>> X,Y=np.meshgrid(x,y)`  
`>>> a=NXdata(np.sin(X)*np.sin(Y), (x,y))`  
`>>> a.nxtree()`  
[`data:NXdata`](data:NXdata)  
`  axis1 = float64(41)`  
`  axis2 = float64(41)`  
`  signal = float64(41x41)`  
`    @axes = axis1:axis2`  
`    @signal = 1`  
`>>> a.nxsum(0).nxtree()`  
[`data:NXdata`](data:NXdata)  
`  axis2 = float64(41)`  
`  signal = float64(41)`  
`    @axes = axis2`  
`    @long_name = Integral from 0.0 to 6.28318530718 `  
`    @signal = 1`

### Arithmetic Operations

#### SDS

Arithmetic operations can be applied to SDS objects in much the same way
as scalars or Numpy arrays that they contain. This includes addition,
subtraction, multiplication and division, either with other SDS objects
or to scalar numbers or Numpy arrays.

`>>> x=SDS(array((1.5,2.5,3.5),name='x')`  
`>>> x`  
`SDS(name=x,value=[ 1.5  2.5  3.5])`  
`>>> x+1`  
`SDS(name=x,value=[ 2.5  3.5  4.5])`  
`>>> 2*x`  
`SDS(name=x,value=[ 3.  5.  7.])`  
`>>> x+x`  
`SDS(name=x,value=[ 3.  5.  7.])`  
`>>> x-x`  
`SDS(name=x,value=[ 0.  0.  0.])`  
`>>> x/x`  
`SDS(name=x,value=[ 1.  1.  1.])`

#### NXdata

Similar operations can also be performed on whole NXdata groups. If two
NXdata groups are to be added, the rank and dimension sizes of the main
signal array must match (although the names could be different).

`>>> y=SDS(np.sin(x),name='y')`  
`>>> y`  
`SDS(name=y,value=[ 0.99749499  0.59847214 -0.35078323])`  
`>>> a=NXdata(y,x)`  
`>>> a.nxtree()`  
[`data:NXdata`](data:NXdata)  
`  x = [ 1.5  2.5  3.5]`  
`  y = [ 0.99749499  0.59847214 -0.35078323]`  
`    @axes = x`  
`    @signal = 1`  
`>>> (a+1).nxtree()`  
[`data:NXdata`](data:NXdata)  
` x = [ 1.5  2.5  3.5]`  
` y = [ 1.99749499  1.59847214  0.64921677]`  
`   @axes = x`  
`   @signal = 1`  
`>>> (2*a).nxtree()`  
[`data:NXdata`](data:NXdata)  
`  x = [ 1.5  2.5  3.5]`  
`  y = [ 1.99498997  1.19694429 -0.70156646]`  
`    @axes = x`  
`    @signal = 1`  
`>>> (a+a).nxtree()`  
[`data:NXdata`](data:NXdata)  
`  x = [ 1.5  2.5  3.5]`  
`  y = [ 1.99498997  1.19694429 -0.70156646]`  
`    @axes = x`  
`    @signal = 1`  
`>>> (a-a).nxtree()`  
[`data:NXdata`](data:NXdata)  
`  x = [ 1.5  2.5  3.5]`  
`  y = [ 0.  0.  0.]`  
`    @axes = x`  
`    @signal = 1`  
`>>> (a/2).nxtree()`  
[`data:NXdata`](data:NXdata)  
`  x = [ 1.5  2.5  3.5]`  
`  y = [ 0.49874749  0.29923607 -0.17539161]`  
`    @axes = x`  
`    @signal = 1`

If data errors are included in the NXdata group (with an additional
array named 'errors'), then the errors are propagated according to the
operand.

`>>> a.nxtree()`  
[`data:NXdata`](data:NXdata)  
`  errors = [ 0.99874671  0.77360981  0.59226956]`  
`  x = [ 1.5  2.5  3.5]`  
`  y = [ 0.99749499  0.59847214  0.35078323]`  
`    @axes = x`  
`    @signal = 1`  
`>>> (a+a).nxtree()`  
[`data:NXdata`](data:NXdata)  
`  errors = [ 1.41244114  1.09404949  0.83759564]`  
`  x = [ 1.5  2.5  3.5]`  
`  y = [ 1.99498997  1.19694429  0.70156646]`  
`    @axes = x`  
`    @signal = 1`