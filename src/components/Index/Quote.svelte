<script>
	export let quote;
	export let writer;
</script>

<blockquote class="sidekick">
	{quote} <cite> {writer}</cite>
</blockquote>

<style>
	.sidekick {
		position: relative;
		padding-left: 1em;
		border-left: 0.2em solid #039be5;
		font-family: 'Roboto', serif;
		font-size: 2.4em;
		line-height: 1.5em;
		font-weight: 100;
	}
	.sidekick:before,
	.sidekick:after {
		font-family: Calibri;
		color: #039be5;
		font-size: 34px;
	}
	.sidekick:before {
		content: '\201e';
	}
	.sidekick:after {
		content: '\201c';
	}
	.sidekick cite {
		font-size: 50%;
		text-align: center;
		top: 50%;
	}
	.sidekick cite:before {
		content: ' \2015 ';
	}
</style>
