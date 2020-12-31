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
* mapbox-gl-js/leaflet/whatever
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
db files are supposedly saved locally (in /code/side projects/atlas-db)

https://medium.com/spatial-data-science/how-to-install-postgis-and-pgadmin4-with-docker-easily-3f4cb3551bef

```
docker run --publish 5433:5433 --volume=pgvolume:/pgdata --env-file=pg-env.list --name=postgres --hostname=postgres --network=pgnetwork --detach crunchydata/crunchy-postgres-gis:centos7-12.5-3.0-4.5.1

docker run --publish 5050:5050 --volume=pga4volume:/var/lib/pgadmin --env-file=pgadmin-env.list --name=pgadmin4 --hostname=pgadmin4 --network=pgnetwork --detach crunchydata/crunchy-pgadmin4:centos7-12.5-4.5.1
```

## `TODO:` now

- [] sketch out db schema
- [] articulate schema in a db migration
- [] load minimal dummy data in a db migration
- [] get sequelize/express talking to PostGIS
- [] create a route to query out the dummy data as geojson
- [] create boilerplate sapper app with a leaflet map
- [] figure out how to manage state in sapper
- [] do something 'reactive'
- [] move db information to enviroment variables

## `TODO:` later

- [] use a service to deploy the thing
- [] roll some auth

