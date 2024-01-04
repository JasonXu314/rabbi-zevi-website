<script lang="ts">
	import { pageTitle } from 'src/lib/stores';

	let fullWidth: number;

	pageTitle.set('Life-Guide “Kabbalah Love”');

	$: width = fullWidth * 0.9;
	$: height = (width * 315) / 560;

	const videos = [
		{ title: 'Intro. to Course - Body/Soul - Love/Fear - Kabbalah Basis', src: 'https://www.youtube.com/embed/XQ_RYDQXJmU?si=-z4Zg8M4HoBy9US6' },
		{ title: 'The Attitude of Gratitude - Integrated Joy', src: 'https://www.youtube.com/embed/Pv-m4s9lv3o?si=26pZD0FEo-7yGzLx' },
		{ title: 'Divine Destiny / Karma - Positive', src: 'https://www.youtube.com/embed/a4cD4wCalsU?si=AU7Zmtz8eptFS5gI' },
		{ title: 'Clear the Slate! - Forgiving', src: 'https://www.youtube.com/embed/aa6bWoFesnM?si=G7cK4Fx2ebN0bH2v' },
		{ title: 'Real, True, Meaningful & Loving Relationships', src: 'https://www.youtube.com/embed/nIUWKOCDM68?si=7keVCbIDtW_49-1u' }
	];
</script>

<h2>7 Options:</h2>
<ol class="root">
	<li>TV Mini- Series (SUMMARY)</li>
	<li>Download Book PDF</li>
	<li>Short Video Course - Link</li>
	<li>36 Vids - Video Course - Link</li>
	<li>Podcast - Live Class</li>
	<li>Book Personal Transformation Course</li>
	<ol>
		<li>The TV Series “Kabbalah Love” Life Course</li>
		<small>Special Thanks To Executive Producer Marc Friedman and the entire SABC team</small>
		<ol class="course" bind:clientWidth={fullWidth}>
			{#each videos as { src, title }}
				<li>{title}</li>
				<iframe
					{width}
					{height}
					{src}
					title="YouTube video player"
					frameborder={0}
					allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
					allowfullscreen
				></iframe>
			{/each}
		</ol>
		<li>BUY</li>
		<li><a href="https://kabbalahwisdom.files.wordpress.com/2017/12/kabbalah-love.pdf">Download FREE Kabbalah-Love PDF Book</a></li>
		<a href="https://kabbalahwisdom.files.wordpress.com/2017/12/kabbalah-love.pdf">
			<img {width} src="https://kabbalahwisdom.files.wordpress.com/2018/01/kaballah.jpg" alt="Kabbalah Lov Book Cover" />
		</a>
		<small>click image to download your PDF Kabbalah, “From Fear To Love” book</small>
		<li><a href="https://kabbalahwisdom.org/kabbalah-life-course-video/">Kabbalah Love Short Video Course</a></li>
		<li><a href="https://www.youtube.com/playlist?list=PLO9RaC58qsh1B7YpDw01KwFEGyAQXJNtV">Kabbalah Love 36 Short Vids</a></li>
		<li>Podcast</li>
		<small><a href="https://kabbalahwisdom.org/kabbalah-love-live-class/">Live Class</a></small>
		<h1><a href="https://kabbalahwisdom.org/testimonials/">TESTIMONIALS</a></h1>
	</ol>
</ol>

<style lang="scss">
	a {
		color: #35845d;
		text-decoration: none;

		&:hover {
			color: hsl(150.37974683544, 59.848484848485%, 61.764705882353%);
		}
	}

	h2 {
		width: 100%;
		box-sizing: border-box;
		background-color: rgb(53, 132, 93);
		padding: 1em 2em;
		color: white;
		margin-bottom: 1em;
	}

	li {
		text-indent: 0.5em;
	}

	@media screen and (max-width: 589px) {
		li {
			text-indent: 0.25em;
		}

		.root {
			ol {
				margin-left: 0.5em;
			}
		}
	}

	.root {
		width: 80%;
		font-size: 1.5rem;
		font-weight: bold;
		margin-bottom: 2em;

		ol {
			margin-left: 1em;

			a {
				display: block;
			}
		}

		.course {
			list-style-type: lower-alpha;
		}
	}
</style>
