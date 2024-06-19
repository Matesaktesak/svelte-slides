<script lang="ts">
	import 'reveal.js/dist/reveal.css';
	import Reveal from 'reveal.js';
	import { onMount, tick } from 'svelte';

	// Import theme
	import 'reveal.js/dist/theme/black.css';

	// Import CSS for plugins
	import 'reveal.js/plugin/highlight/monokai.css';
	
	export let plugins: Reveal.PluginFunction[] = [];
	export let controls: boolean = true;
	export let hash: boolean = true;
	export let autoAnimate: boolean = true;
	export let transition: Reveal.Options["transition"] = 'slide';

	onMount(async () => {
		await tick();
		Reveal.initialize({
			hash,
			plugins,
			controls,
			history: false,
			// slideNumber: true,
			autoAnimate,
			transition,
			...$$restProps
		});
	});
    
	import Presentation from '$lib/Presentation.svelte';
</script>

<div class="reveal" {...$$restProps}>
    <div class="slides">
        <Presentation/>
    </div>
</div>
