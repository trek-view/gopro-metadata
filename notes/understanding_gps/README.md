# 0. Introduction

The global positioning system (GPS) is a network of satellites and receiving devices used to determine the location of something on Earth. Some GPS receivers are so accurate they can establish their location within 1 centimeter (0.4 inches). GPS receivers provide location in latitude, longitude, and altitude. They also provide the accurate time.[ 1 ]

# 1. World Geodetic System

The World Geodetic System (WGS) is a standard for use in cartography, geodesy, and satellite navigation including GPS. This standard includes the definition of the coordinate system's fundamental and derived constants, the normal gravity Earth Gravitational Model (EGM), a description of the associated World Magnetic Model (WMM), and a current list of local datum transformations.[ 2 ]

The latest revision is WGS 84 (also known as WGS 1984 ensemble):

    EPSG:4326 for 2D coordinate reference system (CRS),
    EPSG:4979 for 3D CRS
    EPSG:4978 for geocentric 3D CRS

# 1.1. WGS84

The Global Positioning System(GPS) uses the World Geodetic System (WGS84) as its reference coordinate system.
WGS84 consists of a reference ellipsoid, a standard coordinate system, altitude data, and a geoid.
The error of WGS84 is believed to be less than 2 centimeters to the center mass.
Using geographic coordinate systems, we can define positions on Earth.

The WGS 84 datum surface is an oblate spheroid with equatorial radius a = 6378137 m at the equator and flattening f = 1/298.257223563. The refined value of the WGS 84 gravitational constant (mass of Earth's atmosphere included) is GM = 3986004.418×108 m3/s2. The angular velocity of the Earth is defined to be ω = 72.92115×10−6 rad/s.[ 3 ]

This leads to several computed parameters such as the polar semi-minor axis b which equals a × (1 − f) = 6356752.3142 m, and the first eccentricity squared, e2 = 6.69437999014×10−3.[3] 

# 1.1.1. Latitude/Longitude/Altitude

# 1.1.1.1. Latitude

latitude is a coordinate that specifies the north–south position of a point on the surface of the Earth or another celestial body. Latitude is given as an angle that ranges from –90° at the south pole to 90° at the north pole, with 0° at the Equator. Lines of constant latitude, or parallels, run east–west as circles parallel to the equator.[ 4 ]

- Latitude is specified in degrees.
- North/South
- Run in east-west direction.
- 0°-90°/-90°-90°
- North(+), South(-)

[https://en.wikipedia.org/wiki/File:Latitude_and_longitude_graticule_on_an_ellipsoid.svg](https://en.wikipedia.org/wiki/File:Latitude_and_longitude_graticule_on_an_ellipsoid.svg)

# 1.1.1.2. Longitude

Longitude is a coordinate that specifies the east–west position of a point on the surface of the Earth, or another celestial body. It is an angular measurement, usually expressed in degrees and denoted by the Greek letter lambda (λ). Meridians are semicircular lines running from pole to pole that connect points with the same longitude.[ 5 ]

- Longitude is specified in degrees.
- East/West
- Run in north-south direction.
- East(+), West(-)

# 1.1.1.3. Altitude

Altitude or height (also sometimes known as depth) is a distance measurement, usually in the vertical or "up" direction, between a reference datum and a point or object. The exact definition and reference datum varies according to the context (e.g., aviation, geometry, geographical survey, sport, or atmospheric pressure). Although the term altitude is commonly used to mean the height above sea level of a location, in geography the term elevation is often preferred for this usage.

Vertical distance measurements in the "down" direction are commonly referred to as depth.[ 6 ]

# 1.1.1.4. Equator

The equator represents 0° latitude.

# 1.1.1.5. North/South Poles

North and South Poles represent 90° North and 90° South latitudes.

# 1.1.2. Radians To Degrees

```
degrees = 180.0 / PI * radians
```

# 1.1.3. Degrees To Radians

```
radians = PI / 180.0 * degrees
```

# 1.1.4. DMS

Degrees/Minutes/Seconds

[https://en.wikipedia.org/wiki/Geographic_coordinate_conversion](https://en.wikipedia.org/wiki/Geographic_coordinate_conversion)

# 1.1.5. DD

Decimal/Degrees

[https://en.wikipedia.org/wiki/Geographic_coordinate_conversion](https://en.wikipedia.org/wiki/Geographic_coordinate_conversion)

# 1.2. Geographic coordinate system

The geographic coordinate system (GCS) is a spherical or ellipsoidal coordinate system for measuring and communicating positions directly on the Earth as latitude and longitude.[ 7 ] 

# 1.2.1. Geodetic coordinates

Geodetic coordinates are a type of curvilinear orthogonal coordinate system used in geodesy based on a reference ellipsoid.[ 8 ]

# 1.2.2. Earth-centered, Earth-fixed coordinate system

The Earth-centered, Earth-fixed coordinate system (acronym ECEF), also known as the geocentric coordinate system, is a cartesian spatial reference system that represents locations in the vicinity of the Earth (including its surface, interior, atmosphere, and surrounding outer space) as X, Y, and Z measurements from its center of mass.[ 9 ]

# 1.2.3. ENU

East/North/Up

[https://en.wikipedia.org/wiki/Axes_conventions#Ground_reference_frames:_ENU_and_NED](https://en.wikipedia.org/wiki/Axes_conventions#Ground_reference_frames:_ENU_and_NED)

[https://en.wikipedia.org/wiki/Local_tangent_plane_coordinates](https://en.wikipedia.org/wiki/Local_tangent_plane_coordinates)

# 1.2.4. Coordinate system conversion

[https://en.wikipedia.org/wiki/Geographic_coordinate_conversion](https://en.wikipedia.org/wiki/Geographic_coordinate_conversion)

# 3. References

[1] https://www.nationalgeographic.org/encyclopedia/gps/
[2] https://en.wikipedia.org/wiki/World_Geodetic_System
[3] https://en.wikipedia.org/wiki/World_Geodetic_System#cite_note-Third_Edition_2000-10
[4] https://en.wikipedia.org/wiki/Latitude
[5] https://en.wikipedia.org/wiki/Longitude
[6] https://en.wikipedia.org/wiki/Altitude
[7] https://en.wikipedia.org/wiki/Geographic_coordinate_system#cite_note-chang2016-1
[8] https://en.wikipedia.org/wiki/Geodetic_coordinates
[9] https://en.wikipedia.org/wiki/Earth-centered,_Earth-fixed_coordinate_system