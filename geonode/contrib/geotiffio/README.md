# GeoTIFF.io Contrib App

GeoTIFF.io is a contrib app starting with GeoNode 2.9.  This contrib app adds raster analysis to the GeoNode experience.  It works by adding a link (appearing as a button) to the layer view page of raster layers.  The button is titled 'Analyze with GeoTIFF.io'.  When this button is clicked, it opens up an instance of geotiff.io and loads a GeoTIFF file exported from geoserver using WCS.


## Settings

The relevant section in [settings.py](https://github.com/GeoNode/geonode/blob/master/geonode/settings.py) starts at line [1272](https://github.com/GeoNode/geonode/blob/master/geonode/settings.py#L1272).

```Python

GEOTIFF_IO_ENABLED = strtobool(
    os.getenv('GEOTIFF_IO_ENABLED', 'False')
)

# if your public geoserver location does not use HTTPS,
# you must set GEOTIFF_IO_BASE_URL to use http://
# for example, http://app.geotiff.io
GEOTIFF_IO_BASE_URL = os.getenv(
    'GEOTIFF_IO_BASE_URL', 'https://app.geotiff.io'
)
```

To enable the GeoTIFF.io contrib app set `GEOTIFF_IO_ENABLED` to `True`.

To point the button to another instance of the GeoTIFF.io app, set `GEOTIFF_IO_BASE_URL`.

**Note:** This contrib app does not have to be added to INSTALLED_APPS because it is simply one function and doesn't use templates or the database.

## Cross-Origin Resource Sharing (CORS)
Cross-Origin Resource Sharing (CORS) must be enabled in order for the GeoTIFF.io app to load the data from geoserver.

## GeoTIFF.io
To learn more about GeoTIFF.io visit https://geotiff.io or https://github.com/GeoTIFF/geotiff.io
