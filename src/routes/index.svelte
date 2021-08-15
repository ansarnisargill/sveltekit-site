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
				<section class="m-4" style="display: flex;justify-content: center;">
					<div class="drop-zone-outer">
						<p class="drop-zone-header">Scan your website for potential vulnerabilities.</p>
						<div class="drop-zone-inner">
							<div class="drop-inner-content">
								<div class="select-file-div" />
							</div>
						</div>
						<input
							id="uploadField"
							onchange="onSelectFile()"
							type="file"
							style="visibility:hidden;"
							accept=".pdf"
						/>
						<br />
						<br />
						<button
							class="buy-button-checkout button is-info is-fullwidth"
							id="checkoutBtn"
							onclick="checkOut()">Start Scan</button
						>
					</div>
				</section>
			</div>
		</div>
	</div>
</section>

<style>
  .columns{
    justify-content: center;
  }
	.drop-zone-outer {
		padding: 20px;
		background: #ffffff;
		box-shadow: 0px 20px 20px rgba(2, 1, 45, 0.24);
		border-radius: 10px;
	}

	.drop-zone-header {
		font-family: Roboto;
		font-style: normal;
		font-weight: bold;
		font-size: 24px;
		line-height: 28px;
		color: #000000;
	}

	.drop-zone-inner {
		border: 2px dashed #dfdfdf;
		box-sizing: border-box;
		border-radius: 5px;
	}

	.drop-inner-content {
		text-align: center;
		padding: 7% 0%;
	}

	.select-file-div {
		display: inline-block;
		vertical-align: middle;
	}

	.buy-button-checkout {
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
</style>
