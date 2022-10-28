<script lang="ts">
	import { getComponent } from '../index';

	let component: any;
	export let blok: any;

	if (blok) {
		console.log(blok);
		component = getComponent(blok.component.page);
	} else {
		console.error("Please provide a 'blok' property to the StoryblokComponent");
	}
</script>

<!-- svelte-ignore missing-declaration -->
<svelte:component this={component} {blok} {...$$restProps} />
