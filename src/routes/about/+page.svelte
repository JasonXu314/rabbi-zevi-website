<script lang="ts">
	import { pageTitle } from 'src/lib/stores';

	pageTitle.set('Our Mission');
</script>

<div class="content">
	<span>
		<h1 class="title">Meaningful Books</h1>
		is the publishing house of Rabbi Zevi Wineberg.
	</span>

	<h3 class="bottom">
		Rabbi Zevi Wineberg is the author of over 40 books specializing in taking the content from Jewish mysticism and making it relevant to our modern lives.
	</h3>
</div>

<style lang="scss">
	.content {
		width: 80%;
		font-size: 1.25rem;

		.title {
			display: inline;
			margin-right: 0.25rem;
		}

		.bottom {
			margin-top: 2rem;
		}
	}
</style>
