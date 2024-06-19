<script lang="ts">
	export let url: string;
	export let width: string | number | undefined = "100%";
	export let height: string | number | undefined = undefined;
	export let aspectRatio: string | number | undefined = "16/9";
	const regex = /https:\/\/www\.youtube\.com\/watch\?v=([a-zA-Z0-9]*)/;
	let id: string | null = null;
	const found = url.match(regex);
	if (found) {
		[, id] = found;
	}
</script>

<iframe
	{width}
	{height}
	style:aspect-ratio={aspectRatio}
	src="https://www.youtube.com/embed/{id}"
	title="YouTube video player"
	frameborder="0"
	allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture;"
	allowfullscreen
></iframe>
