### OSM Changeset Viewer on a GL Map

![](https://cloud.githubusercontent.com/assets/126868/24163445/a88728d4-0e90-11e7-9d02-d755b7845c00.png)

Very experimental work in progress. The idea being that you can pass a changeset id and a container HTML element where you want the map rendered, and this plugin should render details of changes made by that changeset in the specified HTML element on a MapboxGL map.

Heavily inspired by the ACHAVI Changeset Viewer: http://wiki.openstreetmap.org/wiki/Achavi

### Use as a module

Create a container div to hold the UI.

```html
<div id='container'></div>
```

```js
var changesetMap = require('changeset-map');
var container = document.getElementById('container');
var changesetMapControl = changesetMap(container, changesetID, { width: '1000px', height: '1000px' });

// binding events
changesetMapControl.on('load', function () {
    changesetMapControl.emit('selectFeature', 'node|way', featureId);
    changesetMapControl.emit('clearFeature');
    changesetMapControl.on('hashchange', function(geometryType, featureId) {
        // update hash.
    });
})
```

For a custom overpass instance, set a `overpassBase` key in the options object. Default instance is https://overpass-api.de/api/interpreter.

### Setup

 Install dependencies using `npm install`.

### Test Locally

Run `npm run start` to start a server and `watchify` process to watch for changes to your files and re-build. Go to the browser at the port where the webserver is running. eg. `http://localhost:8080`

### Build

To build files, run `npm run build`.
