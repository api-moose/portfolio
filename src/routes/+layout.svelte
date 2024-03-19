<script>
	import { fade } from 'svelte/transition';
	import '$lib/styles.css';
	import card from '$lib/thumbnail-portfolio.jpg';
	import Card from '$lib/Card.svelte';
	import { page } from '$app/stores';
	import githubL from '$lib/github-mark-light.png';
	import linkedin from '$lib/linkedin-mark.png';

</script>

<svelte:head>
	<title>Mustafa's Portfolio</title>
	<meta name="description" content="This dynamic portfolio took a while to customize" />
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:site" content="@mustafasmasud" />
	<meta name="twitter:creator" content="@mustafasmasud" />
	<meta name="twitter:title" content="Mustafa's Portfolio" />
	<meta name="twitter:description" content="This dynamic portfolio took a while to customize" />
	<meta name="twitter:image" content="{$page.url.origin}{card}" />
	<meta name="twitter:image:alt" content="An illustration of Mustafa Masud in his 20s" />
</svelte:head>
<Card />

<div class="app">
	<Header />

	<footer>
		<p>visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit</p>
	</footer>
</div>

{#key $page.url.pathname}
    <main in:fade>
        <slot />
    </main>
{/key}

<style>
    header {
        display: flex;
        justify-content: space-between;
    }

    .corner {
        width: 3em;
        height: 3em;
    }

    .icon-link {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        height: 100%;
        transition: transform 0.2s ease;
    }

    .icon-img {
        width: 2em;
        height: 2em;
        object-fit: contain;
        transition: filter 0.2s ease;
    }

    /* Enhanced hover effect for better visibility */
    .icon-link:hover .icon-img {
        filter: brightness(0.7);
        transform: scale(1.1); /* Slightly enlarge the icons on hover */
    }
</style>