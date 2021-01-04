<script>
	import { onMount } from 'svelte'

  // no 'window' server-side
	onMount(async () => {
		const L = await import('leaflet')

    const url = 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png'
	  const attribution = '&copy; <a href="https://osm.org/copyright">OpenStreetMap</a> contributors'

		const map = L.map('map').setView([38, -97], 4)
		L.tileLayer(url, { attribution }).addTo(map)

		// everything and the kitchen sink
		const res = await fetch('http://localhost:3001/journals')
		const journalEntries = await res.json()
		const geojson = journalEntries.map(e => {
			return {
				type: "Feature",
				geometry: e.geom,
				properties: {	memo: e.memo }
			}
		})

		L.geoJSON(geojson).addTo(map)
	})
</script>

<style></style>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
    integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A=="
    crossorigin=""/>

<div id="map" style="height:400px;width:100%"></div>
