grafana-trackmap-panel
======================
A panel for [Grafana](https://grafana.com/) that visualizes GPS points as a line on an interactive map.

Features
--------
- Places a dot on the map at the current time as you mouse over other panels.
- Zoom to a range of points by drawing a box by shift-clicking and dragging.
- Multiple map backgrounds: [OpenStreetMap](http://www.openstreetmap.org/),
  [OpenTopoMap](https://opentopomap.org/), and [Satellite imagery](http://www.esri.com/).
- Track and dot colors can be customized in the options tab.

Screenshots
-----------
![Show current selection as a dot on the map](src/img/topo-crosshair.png)
![Zoom in by selecting a range of points](src/img/topo-boxselect.png)
![Chose what map to display the data on](src/img/satellite-picker.png)

Installation
------------
To use this plugin, clone it into Grafana's plugin directory (you can find this path in Grafana's
logs when it starts up), and build it.

To build, [install npm](https://www.npmjs.com/get-npm) and run the following commands in the
plugin's directory:
```
npm install
npm run build
```

After building, you should now be able to select the "TrackMap" panel when adding a new panel to a
Grafana dashboard.

Configuration
-------------
The plugin requires latitude and longitude measurements provided as floats in two seperate fields.

The following setup has been tested using InfluxDB as a data source in the case where `latitude` and
`longitude` are stored in the `location` table. You will have customize the query for your setup
accordingly.
```
SELECT median("latitude"), median("longitude") FROM "location" WHERE $timeFilter GROUP BY time($interval)
```
