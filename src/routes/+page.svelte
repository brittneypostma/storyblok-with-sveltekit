<script lang="ts">
	import { onMount } from 'svelte';
	import { env } from '$env/dynamic/public';
	import { useStoryblokApi, useStoryblokBridge, storyblokEditable } from '@storyblok/svelte';
	import StoryblokComponent from '$lib/components/StoryblokComponent.svelte';
	import Page from '$lib/components/page.svelte';
	import { getStoryblokApi } from '$lib';

	let story: any = {};

	const storyblokApi = useStoryblokApi();

	async function getStory() {
		try {
			const req = await storyblokApi?.get('cdn/stories/home', {
				version: env.PUBLIC_SPACE_ACCESS_TOKEN
			});
			story = req?.data.story;
			console.log(story);
			useStoryblokBridge(story.id, (newStory) => (story = newStory));
		} catch {
			return new Error('failed');
		}
	}

	onMount(async () => {
		try {
			const req = await storyblokApi?.get('cdn/stories/home', {
				version: env.PUBLIC_SPACE_ACCESS_TOKEN
			});
			story = req?.data.story;
			console.log(story);
			useStoryblokBridge(story.id, (newStory) => (story = newStory));
		} catch {
			return new Error('failed');
		}
	});
</script>

<!-- {#if story}
	<StoryblokComponent blok={story.name} />
{/if} -->

<!-- <div use:storyblokEditable={story.content} /> -->

<!-- {story?.content?.component} -->
