<script lang="ts">
	import AddListing from '$lib/components/Modals/AddListing.svelte';
	import Nav from '$lib/components/nav/Nav.svelte';
	import Welcome from '$lib/components/welcome/Welcome.svelte';
	import * as L from 'leaflet';
	import 'leaflet/dist/leaflet.css';

	let map: any;
	let mounted = true;
	let showAddListing = false;

	function createMap(container: any) {
		let m = L.map(container).setView([-33.8937452, 18.3457911], 9);
		L.tileLayer('https://{s}.basemaps.cartocdn.com/rastertiles/voyager/{z}/{x}/{y}{r}.png', {
			attribution: `&copy;<a href="https://www.openstreetmap.org/copyright" target="_blank">OpenStreetMap</a>,
          &copy;<a href="https://carto.com/attributions" target="_blank">CARTO</a>`,
			subdomains: 'abcd',
			maxZoom: 14
		}).addTo(m);

		return m;
	}

	function mapAction(container: any) {
		map = createMap(container);
		return {
			destroy: () => {
				map.remove();
			}
		};
	}

	function handleOpenAddListing() {
		console.log('handleOpenAddListing');
		showAddListing = !showAddListing;
	}

	function handleNearMe() {
		map.locate({ setView: true, maxZoom: 15 });

		map.on('locationfound', function (e: any) {
			var radius = e.accuracy / 2;
			L.marker(e.latlng)
				.addTo(map)
				.bindPopup('You are within ' + radius + ' meters from this point')
				.openPopup();
		});

		map.on('locationerror', function (e: any) {
			alert('Location access denied.');
		});
	}

	function handleShowWorld() {
		map.setView([0, 0], 2);
	}
</script>

<Nav
	on:add-listing={handleOpenAddListing}
	on:near-me={handleNearMe}
	on:show-world={handleShowWorld}
/>

<!-- <p>add your location to circular</p> -->
<!-- <p>Show locations on map</p> -->
<!-- <p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p> -->

<!-- <div id="map"></div> -->

<div class="welcome-modal">
	<Welcome on:add-listing={handleOpenAddListing} />
</div>

<AddListing open={showAddListing} />

{#if mounted}
	<div style="height:80vh;width:100%" use:mapAction />
{/if}

<style>
	.welcome-modal {
		z-index: 9999;
		position: relative;
	}
</style>
