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

```sh
xcode-select --install
```

Copy and paste into your terminal to download and install Homebrew:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### Installing PostGIS

First, using Homebrew install PostgreSQL:

```sh
brew update
brew doctor
brew install postgresql
```

Install PostGIS

```sh
brew install postgis
```

#### Installing QGIS

First install python

```sh
brew install python
```

QGIS uses numpy, scipy and pyscopg2 which can be installed with pip

```sh
export PYTHONPATH=/usr/local/lib/python2.7/site-packages:$PYTHONPATH
pip install numpy scipy matplotlib processing psycopg2
```

Install GDAL

```sh
brew install gdal
```

Install xquartz

```sh
brew install Caskroom/cask/xquartz
```

Finally, install QGIS and link to the Applications folder

```sh
brew tap osgeo/osgeo4mac
brew install qgis-28
brew linkapps qgis-28
```
