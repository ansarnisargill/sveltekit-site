<script>
	import { goto } from '$app/navigation';
	import { fade } from 'svelte/transition';
	import stringResources from '../stringResources';
</script>

<svelte:head>
	<title>{stringResources.analysisPage.titleTag} - {stringResources.appName}</title>
</svelte:head>

<div class="columns m-4" in:fade>
	<div class="column is-half is-offset-3">
        <div class="box">
            <h4 id="const" class="title is-3">{stringResources.analysisPage.mainTitleText}</h4>
            <article class="message is-primary">
              <div class="message-body">
                {stringResources.analysisPage.mainSubtitleText}
              </div>
            </article>
			<a href="{stringResources.analysisPage.probelyLink}" target="_blank" class="button mt-2 is-outlined">
				{stringResources.analysisPage.openProbelyBtnText}
			</a>
        </div>
	</div>
</div>

<style>
    .title {
		color: var(--textDark);
	}
</style>
