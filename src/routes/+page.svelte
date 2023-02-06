<script lang="ts">
	import Book from 'src/lib/components/Book.svelte';
	import { pageTitle } from 'src/lib/stores';
	import { books } from './books';

	pageTitle.set('Meaningful Books');
</script>

<svelte:head>
	<title>Meaningful Books</title>
</svelte:head>

{#each books as { title, src } (src)}
	<div class="book-entry">
		<Book {title} {src} />
		<h2 class="book-title">{title}</h2>
		<p class="book-description">description here</p>
	</div>
{/each}

<style lang="scss">
	.book-entry {
		width: 80%;
		display: grid;
		grid-template-areas:
			'preview title'
			'preview desc'
			'preview .';
		gap: 0.5rem 2rem;
		grid-template-columns: 1fr 1.5fr;

		.book-title {
			grid-area: title;
			font-size: 1.5rem;
			margin: 0;
			color: #646360;
		}

		.book-description {
			grid-area: desc;
			font-size: 1.25rem;
			color: #646360;
		}

		&:not(:first-of-type) {
			margin-top: 2rem;
		}
	}

	@media screen and (max-width: 1000px) {
		.book-entry {
			grid-template-areas:
				'preview'
				'title'
				'desc';
			gap: 1rem 0;
		}
	}
</style>
