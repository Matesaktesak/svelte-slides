<script lang="ts">
	import Reveal from "reveal.js";
	import { onMount, createEventDispatcher } from "svelte";
	const dispatch = createEventDispatcher();

	// Color Backgrounds
	export let bgColor: string | undefined = undefined;

	// Gradient Backgrounds
	export let bgGradient: string | undefined = undefined;

	// Image Backgrounds
	export let bgImage: string | undefined = undefined;
	export let bgSize: string | undefined = undefined;
	export let bgPosition: string | undefined = undefined;
	export let bgRepeat: string | undefined = undefined;
	export let bgOpacity: string | undefined = undefined;

	// Video Backgrounds
	export let bgVideo: string | undefined = undefined;
	export let bgVideoLoop: boolean | undefined = undefined;
	export let bgVideoMuted: boolean | undefined = undefined;

	// Iframe Backgrounds
	export let bgIframe: string | undefined = undefined;
	export let bgInteractive: string | undefined = undefined;

	// Transitions
	export let animate: boolean | undefined = undefined;

	let slide: HTMLElement;

	export let active: boolean = false;

	onMount(() => {
		Reveal.on('slidechanged', () => {
			const status = slide.classList.contains('present');
			if(status !== active) {
				active = status;
				if(active) dispatch('show'); else dispatch('hide');
			}
		});

		Reveal.on('slidetransitionend', () => {
			if(active) dispatch('transitionEnd');
		});
	});
</script>

<section
	data-background-color={bgColor}
	data-background-gradient={bgGradient}
	data-background-image={bgImage}
	data-background-size={bgSize}
	data-background-position={bgPosition}
	data-background-repeat={bgRepeat}
	data-background-opacity={bgOpacity}
	data-background-video={bgVideo}
	data-background-video-loop={bgVideoLoop}
	data-background-video-muted={bgVideoMuted}
	data-background-iframe={bgIframe}
	data-background-interactive={bgInteractive}
	data-auto-animate={animate}

	bind:this={slide}
>
	<slot />
</section>
