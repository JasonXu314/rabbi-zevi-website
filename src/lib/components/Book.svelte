<script lang="ts">
	export let title: string;
	export let src: string;
</script>

<iframe {title} sandbox="allow-scripts allow-same-origin allow-popups" width="336" height="350" frameborder="0" allowfullscreen style="max-width:100%" {src} />

<style lang="scss">
	iframe {
		grid-area: preview;
	}
</style>
