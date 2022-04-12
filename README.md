README
================

# spectralR: Spectral reflectance visualisations for user-defined areas

## Description

This package provides tools for obtaining, processing, and visualization
of spectral reflectance data for the user-defined polygons of earth
surface classes, allowing to explore visually in which wavelengths the
classes differ. Input should be a shapefile with polygons of surface
classes (it might be polygons of different habitat types, crops, any
other things). As a source of spectral reflectance data we use Sentinel2
L2A satellite mission (only optical bands), obtained through Google
Earth Engine service.

The workflow depends on rgee R package, which provides a bridge between
R and Python API for Google Earth Engine. All the operations with
satellite imageries run in a cloud, and afterwards obtained pixel data
visualize locally. Therefore, despite of extent of input data, the most
resource hungry operations do not overload your local machine. But that
means that you need a stable Internet connection for using API.

For using rgee you should have a Google Earth Engine account. If you
don’t, first register her using your Google account:
<https://earthengine.google.com/new_signup/>

Depends on operating system you use and your current Python
configuration, it may require some additional R and Python packages for
running rgee. See the following links for instructions.

Quick Start User’s Guide for rgee:
<https://www.rdocumentation.org/packages/rgee/versions/1.0.7>

Official documentation for rgee:
<https://r-spatial.github.io/rgee/index.html>

rgee source code: <https://github.com/r-spatial/rgee>

We strongly encourage you to follow official rgee installation guide and
messages arrived during installation process.

The overall workflow is following: 1. Load user’s ESRI shapefile
containing polygons for user-defined surface classes, as well as the
text or numerical field with classes names (labels). 2. Apply rgee
functionality to retrieve multi-band pixel data for classes polygons
from Google Earth Engine service. 3. Visualize retrieved pixel data
locally, mainly using ggplot2 approach.

Essential requirements: - stable Internet connection (for using API) -
Installed and correctly pre-configured Python environment (v. 3.5 or
above) - valid Google Earth Engine account

## Installation

### Install rgee and its basic dependensies

Install and set up rgee

``` r
remotes::install_github("r-spatial/rgee")

# Load the library
library(rgee)

## It is necessary just once to complete installation necessary dependencies
ee_install()
# If something went wrong in this step, see https://r-spatial.github.io/rgee/index.html#installation

# Check non-R dependencies
ee_check() 

# rgee developers recommend installing the version of the Earth Engine Python API
# which rgge was tested with, using the following command
ee_install_upgrade()

# Initialize Google Earth Engine API
ee_Initialize()
```

If everything is OK on this step and you see a message of successful
initiation of API with your GEE username in console, - congratulations,
you managed to install and configure rgee!

## Output examples

![Spectral reflectance curves for user-defined set of habitat
types](https://github.com/olehprylutskyi/habitat-spectral-reflectance/blob/main/SRC_within_bands_S35_S36_R1B_X18_T19_2019_15May-15Jun.png)

![Reflectance per bands for user-defined set of habitat
types](https://github.com/olehprylutskyi/habitat-spectral-reflectance/blob/main/Reflectance_within_bands_S35_S36_R1B_X18_T19_2019_15May-15Jun.png)

![Density of values (as violin plots) for selected habitat types per
band](https://github.com/olehprylutskyi/habitat-spectral-reflectance/blob/main/Violins_R_2019_15May-15Jun.png)

## References

Shyriaieva, D., Prylutskyi, O. (2021). Exploratory analysis of the
spectral reflectance curves of habitat types: a case study on Southern
Bug River valley, Ukraine. In: 63rd IAVS Annual Symposium: Book of
Abstracts, p. 153.
