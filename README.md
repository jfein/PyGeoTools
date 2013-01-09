PyGeoTools
==========

A set of Python tools using geolocation coordinates.

Available tools:
----------

<b>GeoLocation</b> : Class to represent a coordinate on a sphere (most likely Earth). This code was ported to Python directly from http://janmatuschek.de/LatitudeLongitudeBoundingCoordinates, and is owned by Jan Philip Matuschek.

* Instantiating:

```python

loc1 = GeoLocation.from_degrees(26.062951, -80.238853)
loc2 = GeoLocation.from_radians(loc1.rad_lat, loc1.rad_lon)
assert (loc1.rad_lat == loc2.rad_lat and loc1.rad_lon == loc2.rad_lon 
	and loc1.deg_lat == loc2.deg_lat and loc1.deg_lon == loc2.deg_lon)
```

* Distance between instantiated GeoLocation and another GeoLocation

```python

loc1 = GeoLocation.from_degrees(26.062951, -80.238853)
loc2 = GeoLocation.from_degrees(26.060484,-80.207268)
assert loc1.distance_to(loc2) == loc2.distance_to(loc1)
```

* Box that bounds a GeoLocation by a given distance (represented as a SW location and a NE location). All points within the given distance to the GeoLocation are contained in the box.

```python

loc = GeoLocation.from_degrees(26.062951, -80.238853)
distance = 1  # 1 kilometer
SW_loc, NE_loc = loc.bounding_locations(distance)
print loc.distance_to(SW_loc)
print loc.distance_to(NE_loc)
```