# geojson-coords

Extract coordinates from [GeoJSON](http://geojson.org/).

## install

    npm install --save @mapbox/geojson-coords

## api

### `coords(geojson)`

Given any valid GeoJSON object, return a single array of coordinates that
it contains. Handles any root object, collapses multidimensional coordinate arrays
and expands point coordinate arrays.

## example

```js
var geojsonCoords = require('@mapbox/geojson-coords');

geojsonCoords({
    "type": "GeometryCollection",
    "geometries": [
        {
            "type": "Point",
            "coordinates": [100.0, 0.0]
        },
        {
            "type": "LineString",
            "coordinates": [ [101.0, 0.0], [102.0, 1.0] ]
        }
    ]
});
// returns [[100, 0], [101, 0], [102, 1]];

## publishing

Pull Requests to `main` automatically publish a new version based on the PR's title prefix (`major:`, `minor:` or `patch:`) to the npmjs registry.

The published version in the registry is the source of truth for the package version, but you can manually increment the `package.json`'s `version`.

### pre-release versions on other branches

For testing in downstream projects, you can manually trigger the "NPM release" workflow on a branch to publish a pre-release tagged with the short commit sha (e.g. `0.0.2-aa79c6a`) under the npm `prerelease` dist-tag, without affecting `latest`. Check the workflow results for the published version.
