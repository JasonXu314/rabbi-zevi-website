<script lang="ts">
	import { SvelteUIProvider } from '@svelteuidev/core';
	import { pageTitle } from 'src/lib/stores';
	import { onDestroy, onMount } from 'svelte';

	let smol: boolean = false,
		navOpen: boolean = false;

	const listener = () => {
		if (window.innerWidth < 404) {
			smol = true;
		} else {
			smol = false;
		}
	};

	onMount(() => {
		window.addEventListener('resize', listener);

		if (window.innerWidth < 404) {
			smol = true;
		}
	});

	onDestroy(() => {
		if (typeof window !== 'undefined') {
			window.removeEventListener('resize', listener);
		}
	});

	function toggleNav() {
		navOpen = !navOpen;
	}
</script>

<svelte:head>
	<title>{$pageTitle}</title>
</svelte:head>
<SvelteUIProvider withNormalizeCSS>
	<main class="content">
		{#if $pageTitle !== null}
			<h1 class="title">{$pageTitle}</h1>
		{/if}
		<nav class="nav">
			{#if smol}
				<div class="hamburger" class:open={navOpen}>
					<svg class="icon" viewBox="0 0 1024 1024" on:click={toggleNav} on:keyup={(evt) => evt}>
						<title>Menu</title>
						<path
							fill="white"
							class="path1"
							d="M896 307.2h-768c-14.138 0-25.6-11.462-25.6-25.6s11.462-25.6 25.6-25.6h768c14.139 0 25.6 11.462 25.6 25.6s-11.461 25.6-25.6 25.6z"
						/>
						<path
							fill="white"
							class="path2"
							d="M896 563.2h-768c-14.138 0-25.6-11.461-25.6-25.6s11.462-25.6 25.6-25.6h768c14.139 0 25.6 11.461 25.6 25.6s-11.461 25.6-25.6 25.6z"
						/>
						<path
							fill="white"
							class="path3"
							d="M896 819.2h-768c-14.138 0-25.6-11.461-25.6-25.6s11.462-25.6 25.6-25.6h768c14.139 0 25.6 11.461 25.6 25.6s-11.461 25.6-25.6 25.6z"
						/>
					</svg>
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
					</ul>
				</div>
				<button class="donate-button">Donate!</button>
			{:else}
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
			{/if}
		</nav>
		<slot />
	</main>
</SvelteUIProvider>

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

		@media screen and (max-width: 403px) {
			.nav {
				display: flex;
				flex-direction: row;
				justify-content: space-between;

				.hamburger {
					position: relative;

					.icon {
						width: 16px;
						height: 16px;
						padding: 1rem;
						display: block;
					}

					.links {
						display: none;
						position: absolute;
						top: 100%;
						left: 0;
						background-color: #15b6b8;
						flex-direction: column;
						padding: 0.5rem;

						.link {
							padding: 0;

							.link-text {
								padding: 0.5rem 1rem;
								display: block;
							}
						}
					}

					&.open {
						.links {
							display: flex;
						}
					}
				}

				.donate-button {
					color: white;
					background: none;
					border: none;
					padding-right: 2rem;
				}
			}
		}
	}

	@media screen and (max-width: 403px) {
		.content {
			margin: 0 10%;
		}
	}
</style>
