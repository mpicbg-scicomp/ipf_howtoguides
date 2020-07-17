# Open large data
Fiji 
{: .label .label-green }


## Introduction
Datasets which are tens or hundreds of GB usually don't fit into the RAM memory of a computer anymore. Therefore they require special steps when opening in Fiji.

We use the `BioFormats` plugin to open the data. In principle there are two main options:
* *Load data virtually*: Only the current slice is loaded into memory. 
	* Good for previewing the full dataset, but processing options are limited.
* *Load a subset of the data*: Data is cropped in space or time so that it fits into memory.
	* Often, only a small field of view is of actual scientific interest.


**Tip 1:** Acquire also a small test data set when at the microscope (for example with 2 timepoints instead of 100). This test set will make it much less painful to develop an analysis workflow.

**Tip 2:** Use a workstation (like LIPS computers) which has larger RAM memory than your laptop. If you're lucky the data now fits into RAM and you can directly open it normally.

## Step-by-step

* prerequisite: install biofrmats update site

## Alternatives
#### Imaris
* Imaris can handle large data automatically. When opening your data in Imaris for the first time it gets automatically converted (copied) to the proprietary *.ims* format. This is a hierarchical data format which allows for responsive viewing of large data.

#### Fiji BigDataViewer and BigStitcher TODO: image, or make it into main point?
* This option is very useful for exploring the full dataset interactively, especially when the *virtual loading* was too unresponsive. Keep in mind though that it is great for viewing but lacks the usual image procesing features from Fiji (like for example draw and copy a Roi).
* The dataset first needs to be converted to hdf5 format which is a hierarchical data format. Conversion is easiest done with the tools from [*BigStitcher*](https://imagej.net/BigStitcher).
* Activate the *BigStitcher* update site and restart Fiji if needed.
* Then: *Plugins > BigStitcher > Batch Processing > Define Dataset ...*
	* walk through the wizard, try with automatic loading, and resave as hdf5.
* Open your resaved data in [BigDataViewer](https://imagej.net/BigDataViewer): *Plugins > BigDataViewer > OpenXML/HDF5* TODO try this

