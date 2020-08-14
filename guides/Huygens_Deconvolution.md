# Deconvolution using HuygensPro
{: .d-inline-block }

Huygens
{: .label .label-green }


## Introduction
Microscopes produce an image of a real-world object by convolving it with the the so called point spread function (PSF). Deconvolution is a mathematical operation used in image restoration to recover an image that is degraded by this convolution.

The PSF is the 3D blurry image of such a single point light source and is a measure of quality of an optical system. The PSF of a system is mostly determined by the objective used, the wavelength of the light and the refractive index of the immersion and sample media. 

[Huygens](https://svi.nl/Huygens-Professional) software is available at CBG which allows for deconvolution of various types of microscopy images. Additional capabilities include chromatic aberration correction and colocalization analysis. 

For more details on deconvolution check the [documentation from Huygens](https://svi.nl/Huygens-Deconvolution).

### Features of Huygens at CBG
* Currently licenses are available for deconvolution of images acquired through **confocal, spinning disk, widefield** systems. 
* Available in two flavors:
  * **HuygensPro**: GUI-based, useful for exploration of new data
  * **Huygens Remote Manager**: web-based, useful for batch processing 

This how-to guide is about a basic deconvolution pipeline using **HuygensPro**. 


## Step-by-step

> *Prerequisite: Download and install Microsoft Remote Desktop* <br>
> *On Windows, Remote Desktop Client / Connection is installed by default.* <br>
> *On Mac, you need to download and install MRD version 8 or 10 from [here](https://www.techspot.com/downloads/4698-microsoft-remote-desktop-for-mac.html).*

### Step 1: Accessing HuygensPro
* The Huygens software runs on a linux server and can be accessed remotely from your own laptop.
* Book Huygens using the booking database and then use (needs user account)! 
   * The booking database can be reached with this link: [LMF Booking System](https://python-srv1.mpi-cbg.de/lmf-ipf/cgi-bin/index.py). 
   * The service is listed under *Equipments Tab > Computers > Huygens Deconvolution Computer*.

<img src="pics/huygens_deconvolution/huygens_1_access.png" width="500">

* Open Microsoft Remote Desktop.

> *Note that you have to connected to the CBG internal network in order to access the remote desktop. If you are working from an external network, connect to CBG network using a VPN.* 

* (a) Select the PCs tab and click on the *Add PC* button on the main window. Alternatively, one can also click on the '+' button on the top menu bar and select *Add PC*.
* (b) Enter the details.
	* PC Name: huygens-srv1.mpi-cbg.de
	* User account: In drop-down menu, select *Add User Account* and enter relevant credentials. To get the username and password, *contact [us](mailto:ipf@mpi-cbg.de)!*
	* Click on *Add* button at bottom right.  

<table>
<tbody>
  <tr align="center" valign="top"> 
     <td>(a)<br><img src="pics/huygens_deconvolution/huygens_1a_mrdstartup.png"></td>
     <td>(b)<br><img src="pics/huygens_deconvolution/huygens_1b_addpc.png"></td>
  </tr>
</tbody>
</table>

* You will see a computer added to the main window. 

<img src="pics/huygens_deconvolution/huygens_1_mrdwithpc.png" width="300">

* Double click on the added PC to launch the remote desktop. If everything went well, you will have a desktop window like below.

<img src="pics/huygens_deconvolution/huygens_1_remotedesktopview.png" width="400">

### Step 2: Launch HuygensPro 
* Launch Huygens by double-clicking on the *Huygens Professional* icon on the remote desktop.
* The main window has the following appearance. 

<img src="pics/huygens_deconvolution/huygens_2_mainwindow.png" width="400">

* Main sections:
   * The blue region is where you will find the thumbnails of all the opened images. 
   * On the top, you see a ribbon menu, with icons to launch main functions such as deconvolution (*Decon*) and batch processing (*Batch Express*).
   * On the right, the window with multiple tabs gives you information related to the currently selected image. 

<img src="pics/huygens_deconvolution/huygens_2_mainwindowannotated.png" width="400">


### Step 3: Open an image file
* (a) Click on the *Open* button to open an image. Alternative: *File > Open*
   * (b) On opening an LSM image, Huygens will ask for the micrsocope model used for imaging. Select the one you used for image acquisition; contact the LMF if you are not sure.
   * (c) On opening a TIF series, Huygens will ask how to interpret the individual files. Such as slices from a 3D stack, channels or time points.

<table>
<tbody>
  <tr align="center" valign="top"> 
     <td>(a)<br><img src="pics/huygens_deconvolution/huygens_3a_openimage.png"></td>
     <td>(b)<br><img src="pics/huygens_deconvolution/huygens_3b_lsmmenu.png"></td>
  </tr>
  <tr align="center" valign="top"> 
     <td>(c)<br><img src="pics/huygens_deconvolution/huygens_3c_tifseriesmenu.png"></td>
  </tr>
</tbody>
</table>

### Step 4: Inspect your image
* After opening a file, you should find a new image thumbnail in the main work space.

<img src="pics/huygens_deconvolution/huygens_4_imagethumbnail.png" width="400">

* Click on the thumbnail to select the image. 
* Once you select:
   * the right window is updated with the image histogram and other information, and
   * the windows on the left show multiple renderings of the selected image. 
* Right click on the thumbnail and select *2D Visualization > Slicer*. Alternative: *Visualization > Slicer*
* The *Slicer* view which allows you to check if the data was imported properly.

<img src="pics/huygens_deconvolution/huygens_4_slicerview.png" width="400">

* There are controls to select any plane orientation in space (XY, YZ, XZ), zoom, scroll through slices, and view time frames (if applicable).
* Check if the image shows misalignment across the channels in case of multichannel image (chromatic aberration) or drift in Z for 3D time series.

> *Chromatic aberration can be corrected in Huygens using the menu Deconvolution Chromatic Aberration Corrector.*<br>
> *The z-drift corrector tool is available as a part of deconvolution post-process for 3D time-series.*

**Tip**: If the image dimensions are not loaded correctly (for example, channels are read as slices) use the option *Tools > Convert* to set the right dimensions.

### Step 5: Microscopy parameters
* For a good deconvolution result, it is **extremely** important to have accurate microscopic parameters since these values are used to compute the PSF.
* Right-click on the image thumbnail and select *Microscopic parameters*. Alternative: *Edit > Edit Microscopic Parameters*

<img src="pics/huygens_deconvolution/huygens_5_launchmicroscopicparams.png" width="400">

* Parameters are read from the image metadata.
* Sometimes, the values from the metadata are not read out correctly. Check and correct the parameters.

<img src="pics/huygens_deconvolution/huygens_5_parameterwindow.png" width="400">

* (a) Here you can edit the general imaging parameters.
* The most important parameters are the *Sampling Intervals* which have be in a proper range for deconvolution to be possible.

> *Use the [Nyquist Calculator](https://svi.nl/Nyquistcalculator) before your image acquisition to get the sampling limits for your experiment.* 

* (b) Here you can specify the microscope type as well as the excitation and emission wavelength for each acquired channel.

> *For a bandpass emission filter you can use the center wavelength.*<br>
> *Multiphoton images: select Widefield and set the Multi photon excitation to 2.*<br>
> *For standard microscopes the Excitation fill factor = 2 or higher.*<br>
> *For confocal microscope data the Backprojected pinhole (nm) is usually calculated correctly from the metadata.*<br>

* (c) Here you can find the summary of your image data. 

<table>
<tbody>
  <tr align="center" valign="top"> 
     <td>(a)<br><img src="pics/huygens_deconvolution/huygens_5a_parametergeneral.png" width="200" height="300"></td>
     <td>(b)<br><img src="pics/huygens_deconvolution/huygens_5b_parameterchannels.png" width="200" height="300"></td>
  </tr>
  <tr align="center" valign="top"> 
     <td>(c)<br><img src="pics/huygens_deconvolution/huygens_5c_parameterproperties.png" width="200" height="300"></td>
  </tr>
</tbody>
</table>

* Once you have correctly set and verified the parameters, click on *Set all verified* followed by *Accept*. 

> *If you acquired multiple datasets with the same parameters, save them as a template for future use or batch processing.* <br>
> *The Load button serves to load a previously saved parameters template.*

<img src="pics/huygens_deconvolution/huygens_5_parametersverified.png" width="400">

**Tip 1**: For more information on the Huygens microscopic parameters click [here](https://svi.nl/MicroscopicParameters).

**Tip 2**: Huygens uses different background colors and the *Reports* window, to give you feedback about issues with your imaging settings or parameters.   

### Step 6: Deconvolution wizard


 




## Alternatives
List some alternative softwares, troubleshooting tips etc. if applicable

# Various page writing tips
* If an image is too large, specify its size with html import (see start page)
##### **If using header 4 (####), make explicitely bold, otherwise poorly visible**
