+++
author = "Justin Zimmerman"
date = "2015-08-22T10:29:42-04:00"
description = "Installing PostGIS and QGIS using Homebrew."
keywords = ["GIS", "PostGIS", "QGIS"]
tags = ["GIS", "PostGIS", "QGIS"]
title = "Installing PostGIS and QGIS using Homebrew"
topics = ["GIS"]
type = "post"

+++

After browsing the web and seeing outdated information for installing GIS software, I wanted to document the steps I took to install all the required software to get up and running using [Homebrew](http://brew.sh/):

#### Installing Homebrew

Be sure to have xcode installed from Apple
```
xcode-select --install
```

Copy this code a paste into your terminal to download and install Homebrew:
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### Installing PostGIS

First, using Homebrew install PostgreSQL:

```
brew update
brew doctor
brew install postgresql
```
Install PostGIS

```
brew install PostGIS
```

#### Installing QGIS

First install python

```
brew install python
```
QGIS uses numpy, scipy and pyscopg2 which can be installed with pip

```
export PYTHONPATH=/usr/local/lib/python2.7/site-packages:$PYTHONPATH
pip install numpy scipy matplotlib processing psycopg2
```

Install GDAL

```
brew install gdal
```

Install xquartz
```
brew install Caskroom/cask/xquartz
```

Finally, install QGIS and link to the Applications folder
```
brew tap osgeo/osgeo4mac
brew install qgis-28
brew linkapps qgis-28
```
