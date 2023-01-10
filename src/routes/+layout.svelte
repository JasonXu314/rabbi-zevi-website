<script lang="ts">
	import { pageTitle } from 'src/lib/stores';
</script>

<main class="content">
	{#if $pageTitle !== null}
		<h1 class="title">{$pageTitle}</h1>
	{/if}
	<nav class="nav">
		<ul class="links">
			<li class="link">
				<a href="/" class="link-text">Home</a>
			</li>
			<li class="link">
				<a href="/about" class="link-text">About Us</a>
			</li>
			<li class="link">
				<a href="/contact" class="link-text">Contact Us</a>
			</li>
			<li class="link">
				<a href="/courses" class="link-text">Kabbalah/Life Courses</a>
			</li>
			<li class="link donate">
				<button class="link-text">Donate!</button>
			</li>
		</ul>
	</nav>
	<slot />
</main>

<style lang="scss">
	.content {
		background-color: white;
		margin: 0 20%;
		min-height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;

		.title {
			font-size: 4rem;
			margin: 1rem 0 0;
			color: #444340;
		}

		.nav {
			background-color: #15b6b8;
			width: 100%;
			margin-bottom: 2.5rem;

			.links {
				display: flex;
				list-style: none;
				padding: 0;

				.link {
					padding: 0.75rem 0;

					.link-text {
						color: white;
						font-family: 'Source Sans Pro', Helvetica, sans-serif;
						text-decoration: none;
						transition: opacity 0.2s ease;
						font-size: 1.25rem;
						padding: 0.75rem 1rem;
					}

					&.donate {
						margin-left: auto;
						padding: 0 0.5rem;

						.link-text {
							border: none;
							background-color: #15b6b8;
							display: inline;
							cursor: pointer;
						}
					}

					&:hover {
						.link-text {
							opacity: 0.5;
						}
					}
				}
			}
		}
	}
</style>
