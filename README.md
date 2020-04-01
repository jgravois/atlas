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
* supercluster? / vector tiles?
* create a new point
* geocoder
* evergreen browsers only

## v2
* figure out how to deploy it
* optional auth
* edit existing features
* drag and drop GPX/EXIF
* tests

## v?
* `/random` - surprise
* ProseMirror (or similar) rich editor
* fuzzy dates (ie. i dont know when something happened)
* ?
