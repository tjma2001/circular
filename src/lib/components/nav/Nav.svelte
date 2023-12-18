<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	function nearMe() {
		dispatch('near-me');
	}

	function showWorld() {
		dispatch('show-world');
	}

	function addListing() {
		dispatch('add-listing');
	}
</script>

<nav>
	<ul>
		<li><strong>Circular</strong></li>
	</ul>
	<ul>
		<li><a href="#" on:click={nearMe}>&#x1F4CC; Find Near Me</a></li>
		<li><a href="#" on:click={showWorld}>&#x1F30D; World Map</a></li>
		<li><a href="#" role="button" on:click={addListing}>Add a listing</a></li>
	</ul>
</nav>
