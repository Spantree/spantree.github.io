---
layout: post
title: "Provisioning A PostGIS Instance With OpenStreetMap Data"
date: 2013-10-24 10:44
comments: true
published: false
categories: 
---


Sometimes there is no amount of styling you can apply to Google Maps to make it look the way you want.  To really control what is on the page, you will need to create your own maps and serve them up using your own tile server.  But where do you start?

At Spantree, we prefer to stick as much as possible to open source software.  The most widely used open source map tile design software is TileMill, and the only good open source map data is available via the wonderful OpenStreetMap project.  TileMill will allow us to use data from a PostGIS, so as long as we can figure out a way to cram OSM data into a PostGIS server, we should be in business.  


### Setting up a PostGIS server

PostGIS is an extension for PostgreSQL server that turns it into a pretty adavanced GIS server.  On Ubuntu (precise), it's fairly straightforward to install PostreSQL and PostGIS, simply by executing:

```
sudo apt-get install postgresql-9.1 postgresql-9.1-postgis
```

This installs PostreSQL and, among other things, adds some scripts to ``/usr/share/postgresql/9.1/contrib/postgis-1.5/`` that we can use to prepare a database to use for GIS data.  If we log in as the ``postgres`` user (to bypass the inconvenience of having to provide a username and password to the command), we can create a database and quickly turn it into something that is ready to contain GIS data, like so:

```
sudo su postgres
psql -c "create database osm;"
psql -d osm -f /usr/share/postgresql/9.1/contrib/postgis-1.5/postgis.sql
psql -d osm -f /usr/share/postgresql/9.1/contrib/postgis-1.5/spatial_ref_sys.sql
```

### Finding and importing OpenStreetMap Data

A great resource for quickly finding OSM data for a large metro area is the [Metro Extracts](http://metro.teczno.com/ "Metro Extracts") page maintained by Michal Migurski.  Of course, more general [OSM data extracts](http://download.geofabrik.de/) are available and are maintained by Geofabrik.

The two most popular options for importing OSM data into PostgreSQL are [osm2pgsql](http://wiki.openstreetmap.org/wiki/Osm2pgsql) and [imposm](http://imposm.org/).  For us, osm2pgsql worked with the least friction, but your results may vary.  Installing it on Ubuntu 12.04 is straightforward:

```
sudo apt-get install osm2pgsql
```

This installs a somewhat outdated version (for example, the ability to import PBF files is absent), but it's good enough.  We'll use importing the Chicago metro area as an example.  First, we would have to download it (``wget http://osm-extracted-metros.s3.amazonaws.com/chicago.osm.bz2`` works nicely) and then we would import it like so (as postgres user):

```
osm2pgsql -S /usr/share/osm2pgsql/default.style -p chicago -s -d osm chicago.osm.bz2
```

The ``-S`` switch properly points it to the style file, which specifies some options for the import. The switch ``-p`` specifies the prefix that all the tables will have (useful if you're importing multiple data files into the same database).  The ``-s`` specifies "slim mode", which keeps your RAM usage much lower, and ``-d`` specifies the database name.






