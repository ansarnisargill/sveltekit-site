<script>
	import { onMount } from 'svelte';
	import Fa from 'svelte-fa/src/fa.svelte';
	import { faInfo } from '@fortawesome/free-solid-svg-icons';
	import { faLock } from '@fortawesome/free-solid-svg-icons';
	import { faHome } from '@fortawesome/free-solid-svg-icons';

	import { goto } from '$app/navigation';
	import stringResources from '../stringResources';
	onMount(() => {});
	async function gotoHome() {
		await goto('/');
		closeNav();
	}
	async function gotoImpressum() {
		await goto('/impressum');
		closeNav();
	}
	async function gotoDatenschutz() {
		await goto('/datenschutz');
		closeNav();
	}
	function openNav() {
		let x = window.matchMedia('(min-width: 450px)');
		if (x.matches) {
			document.getElementById('mobileNav').style.width = '25%';
		} else {
			document.getElementById('mobileNav').style.width = '100%';
		}
	}

	function closeNav() {
		document.getElementById('mobileNav').style.width = '0%';
	}
</script>

<nav class="navbar main-header is-hidden-mobile" role="navigation">
	<div class="navbar-brand">
		<img class="navbar-item" alt="logo" src="/images/protect.png" on:click={gotoHome} />
	</div>
	<div class="navbar-end ">
		<a class="navbar-item" href="/impressum">
			<span class="icon">
				<Fa icon={faInfo} />
			</span>
			<span>{stringResources.menu.secondBtnText}</span>
		</a>
		<a class="navbar-item" href="/datenschutz">
			<span class="icon">
				<Fa icon={faLock} />
			</span>
			<span>{stringResources.menu.thirdBtnText}</span>
		</a>
	</div>
</nav>
<div id="mobileNav" class="overlay is-hidden-desktop">
	<h1 href="javascript:void(0)" class="closebtn" on:click={closeNav}>&times;</h1>
	<div class="overlay-content">
		<div class="columns m-4">
			<div class=" column is-half p-4">
				<button class="button m-4 is-block" on:click={gotoHome}>
					<span class="icon">
						<Fa icon={faHome} />
					</span>
					<span>{stringResources.menu.firtsBtnText}</span>
				</button>
				<button class="button m-4 is-block" on:click={gotoImpressum}>
					<span class="icon">
						<Fa icon={faInfo} />
					</span>
					<span>{stringResources.menu.secondBtnText}</span>
				</button>
				<button class="button m-4 is-block" on:click={gotoDatenschutz}>
					<span class="icon">
						<Fa icon={faLock} />
					</span>
					<span>{stringResources.menu.thirdBtnText}</span>
				</button>
			</div>
		</div>
	</div>
</div>
<span class="navOpener p-4 is-hidden-desktop" on:click={openNav}>&#9776;</span>

<style>
	.navOpener {
		cursor: pointer;
	}
	button {
		color: black !important;
		background-color: transparent;
		border: none;
		cursor: pointer;
	}
	button:hover {
		color: black !important;
		background-color: rgb(168, 175, 235);
	}
	.overlay {
		height: 100%;
		width: 0;
		position: fixed;
		z-index: 1;
		top: 0;
		left: 0;
		background-color: rgb(0, 0, 0);
		background-color: rgba(0, 0, 0, 0.9);
		overflow-x: hidden;
		transition: 0.5s;
	}

	.overlay-content {
		position: relative;
		top: 5%;
		width: 100%;
		text-align: center;
		margin-top: 30px;
	}

	.overlay .closebtn:hover,
	.overlay .closebtn:focus {
		color: #f1f1f1;
		cursor: pointer;
	}

	.overlay .closebtn {
		position: absolute;
		right: 45px;
		font-size: 60px;
	}

	.main-header {
		height: 80px;
		background: #ffffff;
		box-shadow: 0px 10px 10px rgba(2, 1, 45, 0.06);
		font-family: Roboto;
		font-style: normal;
		font-weight: bold;
		font-size: 16px;
		line-height: 19px;
	}
	@media screen and (max-height: 450px) {
		.overlay .closebtn {
			font-size: 40px;
			right: 35px;
		}
	}
</style>
