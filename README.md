# Python: Basic processing of hyperspectral imagery from AVIRIS-NG collected during ABoVE airborne campaigns

*Date: February 19, 2019*  
*Contact for ORNL DAAC: uso@daac.ornl.gov*  

### Keywords: ABoVE, Airborne, Python

## Overview

Hyperspectral imagery from the Airborne Visible InfraRed Imaging Spectrometer-Next Generation (AVIRIS-NG) was collected as part of the Arctic-Boreal Vulnerability Experiment (ABoVE) in 2017 and 2018 and archived at the ORNL DAAC. File sizes can be prohibitively large due to the large number of raster bands. This tutorial will show users some ways to work with the data in Python.

Read more about ABoVE:                    
https://above.nasa.gov/       
https://daac.ornl.gov/cgi-bin/dataset_lister.pl?p=34               


![Spectra plotted for the center pixel](browse.png)
*Spectral curves extracted for two NGEE Arctic permafrost monitoring sites.*

## Dataset

### ABoVE: Hyperspectral Imagery from AVIRIS-NG for Alaskan and Canadian Arctic   
[10.3334/ORNLDAAC/1569](https://doi.org/10.3334/ORNLDAAC/1569)  

**Abstract**     

This dataset provides Level 1 radiance and Level 2 surface reflectance measured by the Airborne Visible/Infrared Imaging Spectrometer-Next Generation (AVIRIS-NG) instrument during flights over the Arctic-Boreal Vulnerability Experiment (ABoVE) domain between June and August 2017. AVIRIS-NG measures reflected radiance at 5-nanometer (nm) intervals in the visible to shortwave infrared spectral range between 380 and 2510 nm. Measurements are radiometrically and geometrically calibrated and provided at approximately 5-meter spatial resolution. The data include 422 flight lines covering areas of interest to the ABoVE campaign over much of Alaska and western Canada. These data will allow researchers to characterize ecosystem structure and function near the height of the growing season. This dataset represents one part of a multisensor airborne sampling campaign conducted by eleven different aircraft teams for ABoVE.


**Citation**     
Miller, C.E., R.O. Green, D.R. Thompson, A.K. Thorpe, M. Eastwood, I.B. Mccubbin, W. Olson-duvall, M. Bernas, C.M. Sarture, S. Nolte, L.M. Rios, M.A. Hernandez, B.D. Bue, and S.R. Lundeen. 2018. ABoVE: Hyperspectral Imagery from AVIRIS-NG for Alaskan and Canadian Arctic, 2017. ORNL DAAC, Oak Ridge, Tennessee, USA. https://doi.org/10.3334/ORNLDAAC/1569

Please see the **User Guide** for a comprehensive description of this dataset:              
https://daac.ornl.gov/ABOVE/guides/ABoVE_Airborne_AVIRIS_NG.html


## Prerequisites           

### Python 3.x
math, tarfile, json, x, numpy, pandas, gdal/ogr, affine, matplotlib       

### Imagery
Each flight line in the dataset has two corresponding granules, each stored in a zipped tarfile:            
* Level 1 radiance, e.g. ang20180814t224053.tar.gz            
* Level 2 reflectance, e.g. ang20180814t224053rfl.tar.gz     

This tutorial works with the L2 reflectance image for a flight in August during the 2018 campaign. Download the granule at the following link:      
**[https://daac.ornl.gov/daacdata/above/ABoVE_Airborne_AVIRIS_NG/data/ang20180814t224053rfl.tar.gz](https://daac.ornl.gov/daacdata/above/ABoVE_Airborne_AVIRIS_NG/data/ang20180814t224053rfl.tar.gz)** 

Each reflectance tarfile contains two pairs of ENVI (Harris Geospatial) binary image files (no extension) and accompanying header files (.hdr):

**Orthocorrected and atmospherically corrected reflectance data**               
*angYYYYMMDDtHHNNSS_corr_VVV_img (& .hdr*)

Atmospherically corrected water-leaving reflectance (Gao et al. 1993; Thompson et al. 2015); 425 bands at 5-nm intervals in the visible to shortwave infrared spectral range from 380 to 2510 nm

**Orthocorrected water absorption data**                  
*angYYYYMMDDtHHNNSS_h2o_VVV_img (& .hdr*)

Retrieved column water vapor and optical absorption paths for liquid H2O and ice; 3 bands: 1. Column water vapor (cm), 2. Total liquid H2O absorption path (cm), 3. Total ice absorption path (cm)

We only use the orthocorrected and atmospherically corrected reflectance data in this tutorial. Section 2 of the User Guide (linked above) gives a detailed description of the rest of the dataset content, including a list of files found in the L1 radiance tarfiles.


## Tutorial

Download the example granule at the following link:      
**[https://daac.ornl.gov/daacdata/above/ABoVE_Airborne_AVIRIS_NG/data/ang20180814t224053rfl.tar.gz](https://daac.ornl.gov/daacdata/above/ABoVE_Airborne_AVIRIS_NG/data/ang20180814t224053rfl.tar.gz)** 

Open the notebook in your browser here:  
[above-airborne-avirisng-python.ipynb](above-airborne-avirisng-python.ipynb)
