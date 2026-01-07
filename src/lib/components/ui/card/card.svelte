<script lang="ts">
	import type { HTMLAttributes } from "svelte/elements";
	import { cn, type WithElementRef } from "$lib/utils.js";

	let {
		ref = $bindable(null),
		class: className,
		children,
		...restProps
	}: WithElementRef<HTMLAttributes<HTMLDivElement>> = $props();
</script>

<div
	bind:this={ref}
	data-slot="card"
	class={cn(
		"rounded-xl border border-slate-200 bg-card text-card-foreground shadow-sm hover:shadow-md transition-all duration-300 hover:border-slate-300",
		className
	)}
	{...restProps}
>
	{@render children?.()}
</div>
