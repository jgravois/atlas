# atlas

> a time capsule/journal/diary map

as i get closer to 40 i've noticed my memory getting fuzzier and fuzzier. if i dont start writing things down soon i may not get another chance.

i've never made it more than a couple pages into a journal. hopefully my personal atlas will be different.

## status

vaporware with a plan.

## front end routes
* `/` - the map (displays "about" once)
* `/:date/to/:date` - filtered map
* `/:user` - specific user's map
* `/:user/:id` - display a record
* `/:user/#edit` - to add new records
* `/:user/:id#edit` - existing record
* `/about` - explanation

## deps

* PostGIS
* Svelte / Sapper?
* Express
* leaflet
* Docker?
* Sequelize?

## data

* raw EXIF photos
* freehand points
* GPX lines/polygons
* longform text (including embedded external images/emoji)

## db schema

* m:m  user/record relationship
* 1:m record/photo relationship

### columns
* uuid
* timestamp
* geometry
* markdown
* blob?
* createdAt
* updatedAt

## API routes

* `GET /all` - everything and the kitchen sink
* `PUT /:id` - insert a new record
* `POST /:id` - update an existing record
* `GET /:id/next` - chronologically
* `GET /:id/previous` - chronologically
* `GET /` - version etc.
* `GET /ping` - PONG

## v1
* mobile friendly
* renders markdown
* date picker / slider
* create a new point
* geocoder
* evergreen browsers only
* figure out how to deploy it

## v2
* supercluster? / vector tiles?
* optional auth
* edit existing features
* drag and drop GPX/EXIF
* tests

## v?
* `/random` - surprise
* ProseMirror (or similar) rich editor
* fuzzy dates (ie. i dont know when something happened)
* ?

## done

- [x] get docker containers running PostGIS/PGAdmin

followed [these instructions](https://medium.com/spatial-data-science/how-to-install-postgis-and-pgadmin4-with-docker-easily-3f4cb3551bef). db files are supposedly saved locally (in /code/side projects/atlas-db)

```
docker run --publish 5433:5433 --volume=pgvolume:/pgdata --env-file=pg-env.list --name=postgres --hostname=postgres --network=pgnetwork --detach crunchydata/crunchy-postgres-gis:centos7-12.5-3.0-4.5.1

docker run --publish 5050:5050 --volume=pga4volume:/var/lib/pgadmin --env-file=pgadmin-env.list --name=pgadmin4 --hostname=pgadmin4 --network=pgnetwork --detach crunchydata/crunchy-pgadmin4:centos7-12.5-4.5.1
```

- [x] create boilerplate sapper app with a leaflet map ([`atlas@a879111`](https://github.com/jgravois/atlas/commit/a87911123d58c9f1ca870b74d5c2f0efb1444501))
- [x] move db information to enviroment variables
- [x] get sequelize talking to PostGIS - ([`atlas-db@680cd8c`](https://github.com/jgravois/atlas-db/commit/680cd8c8c27726fc0413c8f424ed820686b0bc7f))

followed [these instructions](https://naysan.ca/2020/07/26/upload-a-shapefile-into-a-postgis-table-using-qgis/) to load a dummy shapefile in first

- [x] create an express route to query out geojson

found a [helper library](https://github.com/tommybananas/finale) that scaffolds out a basic REST API from a Sequelize model with minimal boilerplate. Its compatible with Express too, but i started with [restify](https://github.com/restify/node-restify).

## `TODO:` now

- [] sketch out db schema
- [] articulate schema and load dummy data in a migration/seed files
- [] come up with a layout for the app
- [] figure out how to manage state in sapper
- [] do something 'reactive'

## `TODO:` later

- [] use a service to deploy the thing
- [] roll some auth

