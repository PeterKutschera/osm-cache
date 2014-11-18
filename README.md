OSM Tiles cache server

This server is loaded "by hand" with tiles 

Then the tiles are provided from the local store for offline use
   

# Start the osm-cache container
docker run --restart=on-failure:3 -P  -d --name=osm-cache -v $(pwd)/data/OSM:/var/www/OSM peterkutschera/osm-cache

# Load some tiles into the cache:
# World
docker exec osm-cache ./bin/downloadosmtiles.pl --lat -90:90 --lon -180:180 --zoom 0:3 --destdir=/var/www/OSM
# Austria
docker exec osm-cache ./bin/downloadosmtiles.pl --lat 46:49 --lon 9:18 --zoom 4:7 --destdir=/var/www/OSM

