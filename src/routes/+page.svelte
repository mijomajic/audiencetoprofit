<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { Star } from '@lucide/svelte';
</script>

<svelte:head>
	<title>$10k-$50k+ Months in 90 Days | AudienceToProfit</title>
</svelte:head>

<div class="flex flex-col min-h-screen bg-white font-sans text-foreground selection:bg-primary/10">
	<!-- SECTION 1: HERO -->
	<section
		class="relative pt-24 pb-16 md:pt-56 lg:pt-40 md:pb-32 overflow-hidden bg-hero-gradient min-h-screen flex flex-col justify-center"
	>
		<div class="container mx-auto px-6 md:px-4 text-center relative z-10 animate-fade-in-up">
			<!-- Top Label -->
			<div class="mb-6 md:mb-8">
				<span
					class="text-[11px] md:text-sm font-medium uppercase tracking-[0.25em] md:tracking-[0.3em] text-[#8F8F8F] leading-tight"
				>
					FOR FITNESS CREATORS WITH TRACTION
				</span>
			</div>

			<!-- Headline -->
			<h1
				class="text-[36px] md:text-5xl lg:text-6xl font-bold tracking-tight mb-6 md:mb-8 leading-[1.15] md:leading-[1.1] max-w-5xl mx-auto break-words w-full px-2 md:px-0"
			>
				<span class="text-gradient-metallic-dark block"
					>Turn your audience into consistent $10k-$50k+ months in 90 days.</span
				>
			</h1>

			<!-- Subheadline -->
			<p
				class="text-base md:text-xl text-[#8F8F8F] max-w-[700px] mx-auto mb-10 md:mb-12 leading-relaxed font-light px-2 md:px-0"
			>
				I install your product, offer, funnel, email and AI automations so your content stops
				creating "engagement" and starts creating buyers on repeat.
			</p>

			<!-- CTAs -->
			<div class="flex flex-col items-center mb-12 md:mb-20">
				<Button
					href="/apply"
					class="h-14 px-10 text-[15px] font-medium rounded-full bg-white/10 border border-white/25 text-white hover:bg-white/15 hover:shadow-[0_0_20px_rgba(255,255,255,0.1)] transition-all duration-300 backdrop-blur-sm"
				>
					Book a Discovery Call
				</Button>
				<p class="mt-3 md:mt-4 text-sm text-[#8F8F8F] font-light">
					No pressure. It's a discovery call.
				</p>
			</div>

			<!-- Achievements Row -->
			<div class="flex flex-col items-center gap-5 my-0 md:my-6">
				<p
					class="text-sm md:text-lg font-medium tracking-wide text-[#8F8F8F] px-4 md:px-0 leading-relaxed text-center"
				>
					<span class="inline md:inline">10M+ views generated • 6-figures from pipelines</span>
					<span class="block md:inline md:before:content-['_•_'] md:before:mx-1">Ex-CMO</span>
				</p>
			</div>
		</div>
	</section>
</div>
