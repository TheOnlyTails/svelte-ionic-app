<script lang="ts">
	import {
		add,
		logoFacebook,
		logoTwitter,
		code,
		logoVimeo,
		logoGoogle,
		share
	} from 'ionicons/icons';
	import { modalController } from 'ionic-svelte';
	import SourceViewer from '$lib/components/SourceViewer.svelte';

	export let name: string;
	let pulseSourceViewer = false;

	const showSource = async () => {
		const modal = await modalController.create({
			cssClass: 'sourcemodal',
			component: SourceViewer,
			componentProps: { name }
		});
		await modal.present();
	};

	setTimeout(() => {
		pulseSourceViewer = true;
		// and stop the pulse
		setTimeout(() => {
			pulseSourceViewer = false;
		}, 10000);
	}, 20000);
</script>

<div on:click={showSource} on:keyup={showSource}>
	<ion-icon icon={code} class:pulseSourceViewer />
</div>

<style>
	ion-icon {
		font-size: 200%;
	}

	@keyframes shadow-pulse {
		0% {
			box-shadow: 0 0 0 0px rgba(0, 0, 0, 0.2);
		}
		100% {
			box-shadow: 0 0 0 135px rgba(0, 0, 0, 0);
		}
	}

	.pulseSourceViewer {
		border-radius: 50%;
		animation: shadow-pulse 1s infinite;
	}
</style>
