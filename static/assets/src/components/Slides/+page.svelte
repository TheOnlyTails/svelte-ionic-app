<script lang="ts">
	import { menu } from 'ionicons/icons';
	import SourceButton from '$lib/components/SourceButton.svelte';
	import { menuController } from 'ionic-svelte';
	import { IonPage } from 'ionic-svelte';

	let menuIconClicked = false;

	const flipMenuOnOff = () => {
		setTimeout(() => {
			menuController.open('mainmenu');
			if (!menuIconClicked) {
				setTimeout(() => {
					menuController.close('mainmenu');
				}, 2000);
			}
		}, 2000);
	};

	const flipMenuOn = () => {
		menuIconClicked = true;
		menuController.open('mainmenu');
	};
</script>

<svelte:head>
	<title>Ionic Companion - Slides</title>
</svelte:head>

<IonPage>
	<ion-header translucent={true}>
		<ion-toolbar>
			<ion-buttons slot="start">
				<ion-menu-button />
			</ion-buttons>
			<ion-buttons slot="end">
				<SourceButton name="Slides" />
			</ion-buttons>
			<ion-title>Slides</ion-title>
		</ion-toolbar>
	</ion-header>

	<ion-content fullscreen class="ion-padding" scroll-y="false">
		<ion-slides on:ionSlideReachEnd={flipMenuOnOff} pager={true}>
			<ion-slide>
				<img src="../assets/img/slides/slide-1.png" alt="pict" />
				<h2>Welcome!</h2>
				The<b>Ionic UI App</b> is a practical preview of the ionic framework, and a demonstration of
				use in svelte or even other languages. <br />
				<br />
				<br />
			</ion-slide>

			<ion-slide>
				<img src="../assets/img/slides/svelte.png" alt="pict" />
				<h2>Handy tool!</h2>
				By clicking the button bottom right you can instantly view the source code of the element you
				are viewing, to copy/paste and direct link to API docs.<br />
				<br />
				<br />
			</ion-slide>

			<ion-slide>
				<img src="../assets/img/slides/slide-2.png" alt="pict" width="50%" />
				<h2>Easy start</h2>

				<pre>npm create ionic-svelte-app@latest </pre>

				<br />
				<br />
			</ion-slide>

			<ion-slide>
				<img src="../assets/img/slides/slide-4.png" alt="pict" />
				<h2>Ready to Play?</h2>
				Check out
				<ion-icon icon={menu} on:click={flipMenuOn} />
				to look at UI examples. <br />
				<br />
				<br />
				<br />
			</ion-slide>
		</ion-slides>
	</ion-content>
</IonPage>

<style>
	:root {
		--ion-safe-area-top: 20px;
		--ion-safe-area-bottom: 22px;
	}
	ion-slide {
		display: block;
	}
	ion-slide > h2 {
		margin-top: 2.8rem;
	}
	ion-slide > img {
		max-height: 50%;
		max-width: 60%;
		margin: 36px 0;
	}
</style>
