<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
	export let open: boolean;

	const business = {
		name: '',
		location: '',
		phone: '',
		email: '',
		website: '',
		facebook: '',
		instagram: '',
		twitter: '',
		youtube: '',
		tiktok: '',
		products: '',
		description: '',
		yourname: '',
		youremail: '',
		messageToAdmin: ''
	};

	function closeModal() {
		open = false;
	}

	function addListing() {}
</script>

<dialog {open}>
	<article>
		<header>
			<a href="#close" aria-label="Close" class="close" on:click={closeModal}></a>
			Add a listing
		</header>
		<h1>Listing details:</h1>
		<small>
			I will try as hard as possible to quickly verify and add the listings to the website. Please
			give me up to a week to add the items. Usually it should be much quicker. Due to the spam and
			having to verify with the users (if they are not already public) that they want to be uploaded
			here, this might take a little while to get everything verified. If you add a valid email
			address, I will try as much as is possible within my power to keep you updated.
		</small>

		<form class="form">
			<div class="">
				<!-- Markup example 1: input is inside label -->
				<label for="businessname">
					*Business name
					<input
						type="text"
						id="businessname"
						name="businessname"
						placeholder="Business name"
						required
						bind:value={business.name}
					/>
					*Location <span class="subtext">(full location or general area)</span>
					<input
						type="text"
						id="location"
						name="location"
						placeholder="location"
						required
						bind:value={business.location}
					/>
				</label>
			</div>

			<label for="phone">
				Phone number
				<input
					type="text"
					id="phone"
					name="phone"
					placeholder="Phone number"
					required
					bind:value={business.phone}
				/>
			</label>

			<label for="email">
				Email address
				<input
					type="email"
					id="email"
					name="email"
					placeholder="Email address"
					required
					bind:value={business.email}
				/>
			</label>

			<label for="website">
				Website
				<input
					type="text"
					id="website"
					name="website"
					placeholder="Website"
					required
					bind:value={business.website}
				/>
			</label>

			<label for="facebook">
				Facebook
				<input
					type="text"
					id="facebook"
					name="facebook"
					placeholder="Facebook"
					required
					bind:value={business.facebook}
				/>
			</label>

			<label for="instagram">
				Instagram
				<input
					type="text"
					id="instagram"
					name="instagram"
					placeholder="Instagram"
					required
					bind:value={business.instagram}
				/>
			</label>

			<label for="twitter">
				Twitter
				<input
					type="text"
					id="twitter"
					name="twitter"
					placeholder="Twitter"
					required
					bind:value={business.twitter}
				/>
			</label>

			<label for="youtube">
				Youtube
				<input
					type="text"
					id="youtube"
					name="youtube"
					placeholder="Youtube"
					required
					bind:value={business.youtube}
				/>
			</label>

			<label for="tiktok">
				Tiktok
				<input
					type="text"
					id="tiktok"
					name="tiktok"
					placeholder="Tiktok"
					required
					bind:value={business.tiktok}
				/>
			</label>

			<label for="products">
				Products <span class="subtext">(separate with commas)</span>
				<input
					type="text"
					id="products"
					name="products"
					placeholder="Products"
					required
					bind:value={business.products}
				/>
			</label>

			<label for="description">
				Description
				<input
					type="text"
					id="description"
					name="description"
					placeholder="Description"
					required
					bind:value={business.description}
				/>
			</label>

			<hr />

			<label for="yourname">
				*Your name for follow up
				<input
					type="text"
					id="yourname"
					name="yourname"
					placeholder="Your name"
					required
					bind:value={business.yourname}
				/>
			</label>

			<label for="youremail">
				*Your email
				<input
					type="text"
					id="youremail"
					name="youremail"
					placeholder="Your email"
					required
					bind:value={business.youremail}
				/>
			</label>

			<label for="messageToAdmin">
				Message to admin
				<input
					type="text"
					id="messageToAdmin"
					name="messageToAdmin"
					placeholder="Message to admin"
					required
					bind:value={business.messageToAdmin}
				/>
			</label>

			<small>We'll never share your email with anyone else.</small>

			<!-- Button -->
			<button type="submit">Submit</button>
		</form>
	</article>
</dialog>

<style>
	.form {
		margin-top: 2rem;
	}
	.subtext {
		font-size: small;
	}
</style>
