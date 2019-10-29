# Convert Hong Kong 1980 Grid System to World Geodetic System

## Hong Kong 1980 Grid System
Hong Kong 1980 Grid System (EPSG:2326) is the reference coordinate system used by Lands Department, HKSARG.

## World Geodetic System
The latest revision, WGS 84 (EPSG:4326), is the reference coordinate system used by the Global Positioning System (GPS).

# Language
* [HTTP](#http)
* [Javascript](#javascript)
* [Python](#python)

## HTTP
RESTful API provided by Geodetic Survey Section, Lands Department, HKSARG. [API Manual](https://www.geodetic.gov.hk/transform/tformAPI_manual.pdf)

Request
```http
GET https://www.geodetic.gov.hk/transform/v2/?inSys=hkgrid&outSys=wgsgeog&e=835411.431&n=817266.016
```
Response
```json
{
  "wgsLat": 22.294313001,
  "wgsLong": 114.168562005
}
```

## Javascript
[PROJ4JS](http://proj4js.org)
```js
var proj4 = require('proj4');

proj4.defs('EPSG:2326', '+proj=tmerc +lat_0=22.31213333333334 +lon_0=114.1785555555556 +k=1 +x_0=836694.05 +y_0=819069.8 +ellps=intl +towgs84=-162.619,-276.959,-161.764,0.067753,-2.24365,-1.15883,-1.09425 +units=m +no_defs');

var result = proj4('EPSG:2326', 'EPSG:4326', [easting, northing]);

var longitude = result[0];
var latitude = result[1];

```

## Python
[pyproj](https://pyproj4.github.io/pyproj)
```py
from pyproj import Transformer
transformer = Transformer.from_crs(2326, 4326)

latitude, longitude = transformer.transform(northing, easting)
```
