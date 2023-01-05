<script>
	import Book from 'src/lib/components/Book.svelte';
	import { books } from './books';
</script>

<svelte:head>
	<title>Meaningful Books</title>
</svelte:head>

<div class="main">
	<h1 class="title">Meaningful Books</h1>
	{#each books as { title, src } (src)}
		<div class="book-entry">
			<Book {title} {src} />
			<h2 class="book-title">{title}</h2>
			<p class="book-description">description here</p>
		</div>
	{/each}
</div>

<style lang="scss">
	.main {
		display: flex;
		flex-direction: column;
		align-items: center;

		.title {
			font-size: 4rem;
			margin: 1rem;
			color: #444340;
		}

		.book-entry {
			width: 80%;
			display: grid;
			grid-template-areas:
				'preview title'
				'preview desc'
				'preview .';
			gap: 1rem 2rem;

			.book-title {
				grid-area: title;
				font-size: 2rem;
				margin: 0;
				color: #444340;
			}

			.book-description {
				grid-area: desc;
				font-size: 1.5rem;
				color: #444340;
			}

			&:not(:first-of-type) {
				margin-top: 2rem;
			}
		}
	}
</style>
