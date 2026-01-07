<script lang="ts">
	import { Check, Clock, FileText, CreditCard } from '@lucide/svelte';
</script>

<svelte:head>
	<title>Apply for the Revenue Engine | AudienceToProfit</title>
</svelte:head>

<div class="min-h-screen bg-hero-gradient relative overflow-hidden pt-32 md:pt-36 pb-10">
	<div class="container mx-auto max-w-5xl px-6 md:px-4 animate-fade-in-up">
		<!-- Intro Header -->
		<section class="text-center mb-12">
			<h1
				class="text-[36px] md:text-5xl font-bold tracking-tight mb-4 md:mb-6 text-white text-gradient-metallic-dark block py-2 overflow-visible leading-[1.15]"
			>
				Apply for the <br class="md:hidden" /> 90-Day Revenue Engine
			</h1>
			<p class="text-base md:text-xl text-[#8F8F8F] max-w-2xl mx-auto leading-relaxed">
				This is a 30-minute call to diagnose where your attention is leaking and map the system to
				turn it into revenue.
			</p>
		</section>

		<!-- Calendly Embed -->
		<section class="mb-0 flex justify-center w-full px-0 md:px-0">
			<!-- Calendly inline widget begin -->
			<div
				class="calendly-inline-widget w-full h-[950px] md:h-[1200px]"
				data-url="https://calendly.com/audiencetoprofit/a2p-discovery?hide_gdpr_banner=1&background_color=141414&text_color=ffffff&primary_color=ffffff"
				style="min-width:320px;"
			></div>
			<script
				type="text/javascript"
				src="https://assets.calendly.com/assets/external/widget.js"
				async
			></script>
			<!-- Calendly inline widget end -->
		</section>
	</div>
</div>
