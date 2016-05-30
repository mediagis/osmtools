# osmtools
Command line tools to work with OSM files in docker.

# Image description
This image contains the following comand line utilities:
* [osmconvert](http://wiki.openstreetmap.org/wiki/Osmconvert) - can be used to convert and process OpenStreetMap files.
* [osmfilter](http://wiki.openstreetmap.org/wiki/Osmfilter) - is a command line tool used to filter OpenStreetMap data files for specific tags.
* [osmupdate](http://wiki.openstreetmap.org/wiki/Osmupdate) - downloads and cumulates OSM Changefiles of different categories (minutely, hourly, daily).

# How to use this image

Prepare yours data:

```
mkdir -p /data/osm-data
wget http://download.geofabrik.de/europe/monaco-latest.osm.pbf -O /data/osm-data/monaco.osm.pbf
```

Mount host directory with data into container `/osm` and work with `osmconvert` `osmfilter` or `osmupdate` utils.

**Retrieving Statistical Data**
```
docker run --rm  -it --volume /data/osm-data:/osm mediagis/osmtools osmconvert --out-statistics monaco.osm.pbf
```

**Convert from osm.pbf to o5m**

```
docker run --rm  -it --volume /data/osm-data:/osm mediagis/osmtools osmconvert monaco.osm.pbf -o=monaco.o5m
```

**List of all keys sorted by occurrence**

```
docker run --rm  -it --volume /data/osm-data:/osm mediagis/osmtools osmfilter --out-count monaco.o5m
```

# User Feedback

**Issues**

If you have any problems or questions about this image, please contact me through a [issue](https://github.com/mediagis/osmtools/issues) or email [pipetc@gmail.com](mailto:pipetc@gmail.com).
