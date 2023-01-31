<script lang="ts">
	import { onMount } from 'svelte';

	export let title: string;
	export let src: string;

	let width: number = 336;
	let height: number = 350;

	onMount(() => {
		if (window.innerWidth < 768) {
			width = window.innerWidth * 0.8 - 60;
			height = width * 1.05;
		}
	});
</script>

<iframe {title} sandbox="allow-scripts allow-same-origin allow-popups" {width} {height} frameborder={0} allowfullscreen style="max-width:100%" {src} />

<style lang="scss">
	iframe {
		grid-area: preview;
	}
</style>
