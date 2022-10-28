<script lang="ts">
	import '../app.postcss';
	import { useStoryblokBridge } from '@storyblok/svelte';
	import { onMount } from 'svelte';
	import { env } from '$env/dynamic/public';
	import Feature from '$lib/components/feature.svelte';
	import Grid from '$lib/components/grid.svelte';
	import Page from '$lib/components/page.svelte';
	import Teaser from '$lib/components/teaser.svelte';
	import { apiPlugin, storyblokInit } from '@storyblok/svelte';

	storyblokInit({
		accessToken: env.PUBLIC_SPACE_ACCESS_TOKEN,
		apiOptions: {
			//storyblok-js-client config object
			cache: { type: 'memory' }
		},
		use: [apiPlugin],
		components: {
			feature: Feature,
			grid: Grid,
			page: Page,
			teaser: Teaser
		}
	});

	// let { story } = data;
	// onMount(() => {
	// 	useStoryblokBridge(story.id, (newStory) => (story = newStory));
	// });
</script>

<main class="prose prose-xl">
	<slot />
</main>
