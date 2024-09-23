<script lang="ts">
	import { cn } from "$lib/utils.js";

	export let className: string = "";
	export let src: string = "";
	export let alt: string = "";
	export { className as class };
</script>

<img
	src={src}
	{alt}
	class={cn("aspect-square h-full w-full", className)}
	{...$$restProps}
/>
