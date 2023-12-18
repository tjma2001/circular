<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	function closeModal() {
		const dialog = document.querySelector('dialog');
		if (dialog) {
			dialog.close();
		}
	}

	function addListing() {
		const dialog = document.querySelector('dialog');
		if (dialog) {
			dialog.close();
		}

		// emit event to parent to open add-listing dialog
		dispatch('add-listing');
	}
</script>

<dialog open>
	<article>
		<header>
			<a href="#close" aria-label="Close" class="close" on:click={closeModal}></a>
			Circular
		</header>
		<h1>Welcome to circular</h1>
		<p>
			Circular is a list of businesses that represent users that provide services in the new
			circular economy ;-)
		</p>
		<p>
			Please feel free to browse the listings. If there are any businesses that you know of that
			wish to be listed here, please either contact them to add them here or add them here on their
			behalf if you have their blessing.
		</p>
		<p>
			<button on:click={closeModal}>browse listings</button>
			<button on:click={addListing}>add listing</button>
		</p>

		<p>leave a tip: btcaddressgoeshere</p>
	</article>
</dialog>

<style>
	dialog {
		border: 0;
		border-radius: 1rem;
		box-shadow: 0 0 1rem rgba(0, 0, 0, 0.25);
	}
</style>
