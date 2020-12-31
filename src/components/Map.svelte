<script>
	import { onMount } from 'svelte';

  // no 'window' server-side
	onMount(async () => {
		const L = await import('leaflet')

    const url = 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png'
	  const attribution = '&copy; <a href="https://osm.org/copyright">OpenStreetMap</a> contributors'

		const map = L.map('map').setView([37.75, -122.23], 10)
		L.tileLayer(url, { attribution }).addTo(map)
	});
</script>

<style></style>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
    integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A=="
    crossorigin=""/>

<div id="map" style="height:400px;width:100%"></div>
