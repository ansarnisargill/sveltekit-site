<script>
	import { goto } from '$app/navigation';
	import { fade } from 'svelte/transition';
	import stringResources from '../stringResources';
	import Navbar from '../components/Navbar.svelte';
	import Banner from '../components/Index/Banner.svelte';
	import Quote from '../components/Index/Quote.svelte';

	let showAlert = false;
	async function scanSite() {
		let url = document.getElementById('url').value;
		if (url == null || url == '') {
			showAlert = true;
			return;
		}
		await goto(`/result?url=${url}`);
	}
</script>

<svelte:head>
	<title>{stringResources.appName} - {stringResources.indexPage.title}</title>
</svelte:head>

{#if showAlert}
	<div class="notification is-danger" in:fade>
		<button class="delete" on:click={() => (showAlert = false)} />
		{stringResources.indexPage.urlMissingMsg}
	</div>
{/if}

<Navbar />

<section class="hero is-default is-bold">
	<div class="hero-body">
		<div class="columns">
			<div class="column is-6">
				<section>
					<Banner appName={stringResources.appName} />

					<Quote quote={stringResources.indexPage.aboutText} writer={'Keywan Ghadami'} />
				</section>
				<section class="scan-div">
					<div class="zone-outer">
						<p class="zone-header mt-3">Scan your website for potential vulnerabilities.</p>

						<input id="url" placeholder={stringResources.indexPage.scanInputPlaceHolder} type="text" class="mt-3" />
						<button class="scan-button button is-info is-fullwidth mt-4" on:click={scanSite} >
							Start Scan
						</button>
					</div>
				</section>
			</div>
		</div>
	</div>
</section>

<style>
	.columns {
		justify-content: center;
	}
	.scan-div {
		display: flex;
		justify-content: center;
		margin-top: 4rem;
	}
	.zone-outer {
		padding: 20px;
		background: #ffffff;
		box-shadow: -1px 10px 20px rgba(2, 1, 45, 0.24);
		border-radius: 10px;
	}

	.zone-header {
		font-family: Roboto;
		font-style: normal;
		font-weight: bold;
		font-size: 24px;
		line-height: 28px;
		color: #000000;
	}

	.scan-button {
		background: rgba(57, 119, 240, 1);
		border-radius: 5px;
		border-style: none;
		font-family: Roboto;
		font-style: normal;
		font-weight: bold;
		font-size: 20px;
		line-height: 23px;
		text-align: center;
		color: #ffffff;
	}
	#url {
		height: 4rem;
		width: 100%;
		border-style: dotted;
		font-size: 2rem;
	}
	#url:focus{
		border:double;
	}
	#url::placeholder{
		padding: 10px;
	}
</style>
