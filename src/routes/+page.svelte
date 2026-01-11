<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { Star } from '@lucide/svelte';
	import { onMount } from 'svelte';

	let visibleSteps = new Set();
	let heroVisible = false;
	let processHeaderVisible = false;
	let finalCTAVisible = false;

	onMount(() => {
		const observerOptions = {
			threshold: 0.1
		};

		const observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					if (entry.target.id === 'hero-content') heroVisible = true;
					if (entry.target.id === 'process-header') processHeaderVisible = true;
					if (entry.target.id === 'final-cta') finalCTAVisible = true;
					if (entry.target instanceof HTMLElement && entry.target.dataset.step) {
						visibleSteps.add(entry.target.dataset.step);
						visibleSteps = visibleSteps; // trigger reactivity
					}
				}
			});
		}, observerOptions);

		const hero = document.getElementById('hero-content');
		const processHeader = document.getElementById('process-header');
		const finalCta = document.getElementById('final-cta');
		const steps = document.querySelectorAll('[data-step]');

		if (hero) observer.observe(hero);
		if (processHeader) observer.observe(processHeader);
		if (finalCta) observer.observe(finalCta);
		steps.forEach((step) => observer.observe(step));

		return () => observer.disconnect();
	});
</script>

<svelte:head>
	<title>DFY Cold Email Systems - 15 Prospects in 60 Days | Eastline Consulting</title>
</svelte:head>

<div class="flex flex-col min-h-screen bg-white font-sans text-foreground selection:bg-primary/10">
	<!-- SECTION 1: HERO -->
	<section
		class="relative pt-24 pb-16 md:pt-56 lg:pt-40 md:pb-32 overflow-hidden bg-hero-gradient min-h-screen flex flex-col justify-center"
	>
		<div
			id="hero-content"
			class="container mx-auto px-6 md:px-4 text-center relative z-10 transition-[opacity,transform] duration-1000 ease-out {heroVisible
				? 'opacity-100 translate-y-0'
				: 'opacity-0 translate-y-8'}"
		>
			<!-- Elevated Achievements Row (Eyebrow) -->
			<div
				class="flex items-center justify-center gap-6 md:gap-10 mb-8 delay-100 duration-1000 transition-[opacity,transform] {heroVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<div class="flex items-center gap-3">
					<div
						class="w-2 h-2 rounded-full bg-white/10 flex items-center justify-center border border-white/10"
					>
						<div
							class="w-1 h-1 rounded-full bg-white/40 shadow-[0_0_8px_rgba(255,255,255,0.3)]"
						></div>
					</div>
					<span
						class="text-[11px] md:text-[13px] font-bold uppercase tracking-[0.3em] text-white/90 mr-[-0.3em]"
						>Ex-CMO</span
					>
				</div>
				<div class="flex items-center gap-3">
					<div
						class="w-2 h-2 rounded-full bg-white/10 flex items-center justify-center border border-white/10"
					>
						<div
							class="w-1 h-1 rounded-full bg-white/40 shadow-[0_0_8px_rgba(255,255,255,0.3)]"
						></div>
					</div>
					<span
						class="text-[11px] md:text-[13px] font-bold uppercase tracking-[0.3em] text-white/90 mr-[-0.3em]"
						>$250k Generated</span
					>
				</div>
			</div>

			<!-- Headline -->
			<h1
				class="text-[28px] min-[390px]:text-[32px] md:text-5xl lg:text-6xl font-bold tracking-tight mb-6 md:mb-8 leading-[1.15] md:leading-[1.1] max-w-5xl mx-auto break-words w-full px-2 md:px-0 delay-300 duration-1000 transition-[opacity,transform,filter] {heroVisible
					? 'opacity-100 translate-y-0 blur-0'
					: 'opacity-0 translate-y-8 blur-[10px]'}"
			>
				<span class="text-gradient-metallic-dark block"
					>DFY cold email systems that put 15 qualified prospects in your inbox in 60 days or less -
					guaranteed</span
				>
			</h1>

			<!-- Subheadline -->
			<p
				class="text-base md:text-xl text-[#8F8F8F] max-w-[700px] mx-auto mb-10 md:mb-12 leading-relaxed font-light px-2 md:px-0 [text-wrap:balance] delay-500 duration-1000 transition-[opacity,transform,filter] {heroVisible
					? 'opacity-100 translate-y-0 blur-0'
					: 'opacity-0 translate-y-8 blur-[5px]'}"
			>
				We build the system, launch it, and put qualified prospects in your inbox while you focus on
				closing. If we fail our promise we give you a full refund.
			</p>

			<!-- CTAs -->
			<div
				class="flex flex-col items-center mb-12 md:mb-20 delay-700 duration-1000 transition-[opacity,transform] {heroVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<Button
					href="https://calendly.com/eastlineconsulting/30min"
					target="_blank"
					class="h-14 px-10 text-[15px] font-medium rounded-full bg-white/10 border border-white/25 text-white hover:bg-white/15 hover:shadow-[0_0_20px_rgba(255,255,255,0.1)] transition-[background-color,box-shadow,transform,border-color] duration-300 backdrop-blur-sm animate-shine"
				>
					Get your 15 prospects
				</Button>
				<p class="mt-3 md:mt-4 text-sm text-[#8F8F8F] font-light">See if you qualify.</p>
			</div>
		</div>

		<div
			class="absolute bottom-8 md:bottom-10 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 md:gap-3 delay-[1200ms] duration-1000 transition-[opacity,transform] {heroVisible
				? 'opacity-100 translate-y-0'
				: 'opacity-0 translate-y-4'}"
		>
			<div class="flex flex-col items-center gap-2">
				<span class="text-[10px] font-bold tracking-[0.2em] uppercase text-[#8F8F8F] mr-[-0.2em]">
					See how it works
				</span>
				<div class="flex items-center justify-center h-6">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="18"
						height="18"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						class="text-[#8F8F8F] animate-bounce"
					>
						<path d="M7 13l5 5 5-5" />
					</svg>
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 2: THE PROCESS -->
	<section class="pt-24 pb-12 bg-white overflow-hidden">
		<div class="container mx-auto px-6 md:px-4 max-w-4xl">
			<div
				id="process-header"
				class="text-center mb-24 transition-[opacity,transform] duration-1000 ease-out {processHeaderVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<h2 class="text-3xl md:text-5xl font-bold tracking-tight mb-4 text-[#141414]">
					The entire process
				</h2>
				<p
					class="text-[#8F8F8F] text-lg max-w-2xl mx-auto font-light border-b border-[#EBEBEB] pb-12"
				>
					How we build your high-converting customer acquisition engine.
				</p>
			</div>

			<div class="space-y-16">
				<!-- Step 01 -->
				<div
					data-step="1"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-[cubic-bezier(0.16,1,0.3,1)] flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'1'
					)
						? 'opacity-100 translate-y-0 scale-100 blur-0'
						: 'opacity-0 translate-y-12 scale-[0.98] blur-[1px]'}"
				>
					<!-- Shine Effect -->
					<div
						class="absolute inset-0 bg-gradient-to-tr from-transparent via-white/20 to-transparent -translate-x-full group-hover:translate-x-full transition-transform duration-1000 ease-in-out pointer-events-none"
					></div>

					<div
						class="inline-block px-3 py-1 bg-[#141414]/10 text-[#141414] text-[10px] font-bold tracking-[0.2em] uppercase rounded-full mb-8 backdrop-blur-md border border-[#141414]/5"
					>
						Step 01
					</div>
					<h3 class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight">
						Market-Match Blueprint
					</h3>
					<p class="text-[#4A4A4F] text-lg leading-relaxed mb-10 font-normal max-w-2xl md:px-4">
						Before sending any emails, we define the strategy: your ICP, your offer, and the angle
						that makes prospects care. Here, we create clarity, stand out, and craft a message
						that’s hard to ignore.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-8"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-[opacity,transform] duration-700 delay-[600ms] {visibleSteps.has(
								'1'
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							ICP + buyer psychology
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-[opacity,transform] duration-700 delay-[700ms] {visibleSteps.has(
								'1'
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Offer positioning
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-[opacity,transform] duration-700 delay-[800ms] {visibleSteps.has(
								'1'
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Campaign goals
						</span>
					</div>
				</div>

				<!-- Step 02 -->
				<div
					data-step="2"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-out flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'2'
					)
						? 'opacity-100 translate-y-0 scale-100 blur-0'
						: 'opacity-0 translate-y-12 scale-[0.98] blur-[1px]'}"
				>
					<div
						class="absolute inset-0 bg-gradient-to-tr from-transparent via-white/20 to-transparent -translate-x-full group-hover:translate-x-full transition-transform duration-1000 ease-in-out pointer-events-none"
					></div>
					<div
						class="inline-block px-3 py-1 bg-[#141414]/10 text-[#141414] text-[10px] font-bold tracking-[0.2em] uppercase rounded-full mb-8 backdrop-blur-md border border-[#141414]/5"
					>
						Step 02
					</div>
					<h3 class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight">
						Signal-Driven Lead Intelligence
					</h3>
					<p class="text-[#4A4A4F] text-lg leading-relaxed mb-10 font-normal max-w-2xl md:px-4">
						Generic lists yield generic results. We build a precise prospect database based on role,
						relevance, and buying signals. Then we verify it to keep your campaigns clean, accurate,
						and scalable.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-8"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							High quality lead list
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Verification + Anti-bounce
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Segments by industry & title
						</span>
					</div>
				</div>

				<!-- Step 03 -->
				<div
					data-step="3"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-out flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'3'
					)
						? 'opacity-100 translate-y-0 scale-100 blur-0'
						: 'opacity-0 translate-y-12 scale-[0.98] blur-[1px]'}"
				>
					<div
						class="absolute inset-0 bg-gradient-to-tr from-transparent via-white/20 to-transparent -translate-x-full group-hover:translate-x-full transition-transform duration-1000 ease-in-out pointer-events-none"
					></div>
					<div
						class="inline-block px-3 py-1 bg-[#141414]/10 text-[#141414] text-[10px] font-bold tracking-[0.2em] uppercase rounded-full mb-8 backdrop-blur-md border border-[#141414]/5"
					>
						Step 03
					</div>
					<h3 class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight">
						Deliverability Fortress Setup
					</h3>
					<p class="text-[#4A4A4F] text-lg leading-relaxed mb-10 font-normal max-w-2xl md:px-4">
						We design a sending system to consistently land in the primary inboxes, not spam. This
						includes dedicated sending domains, professional inboxes, and full authentication
						(SPF/DKIM/DMARC), plus a warm-up protocol to protect your reputation.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-8"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Multi-domain + multi-inbox
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							SPF, DKIM, DMARC setup
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Warmup + Inbox health
						</span>
					</div>
				</div>

				<!-- Step 04 -->
				<div
					data-step="4"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-out flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'4'
					)
						? 'opacity-100 translate-y-0 scale-100 blur-0'
						: 'opacity-0 translate-y-12 scale-[0.98] blur-[1px]'}"
				>
					<div
						class="absolute inset-0 bg-gradient-to-tr from-transparent via-white/20 to-transparent -translate-x-full group-hover:translate-x-full transition-transform duration-1000 ease-in-out pointer-events-none"
					></div>
					<div
						class="inline-block px-3 py-1 bg-[#141414]/10 text-[#141414] text-[10px] font-bold tracking-[0.2em] uppercase rounded-full mb-8 backdrop-blur-md border border-[#141414]/5"
					>
						Step 04
					</div>
					<h3 class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight">
						Belief-Shift Copy System
					</h3>
					<p class="text-[#4A4A4F] text-lg leading-relaxed mb-10 font-normal max-w-2xl md:px-4">
						Our emails aim to start conversations, not sound overly marketing-focused. We use
						direct-response principles to create relevance quickly, reduce friction, and earn
						replies. Backed by proof and a clear explanation of why your offer works.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-8"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Direct-response writing
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Objection handling
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Personalization frameworks
						</span>
					</div>
				</div>

				<!-- Step 05 -->
				<div
					data-step="5"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-out flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'5'
					)
						? 'opacity-100 translate-y-0 scale-100 blur-0'
						: 'opacity-0 translate-y-12 scale-[0.98] blur-[1px]'}"
				>
					<div
						class="absolute inset-0 bg-gradient-to-tr from-transparent via-white/20 to-transparent -translate-x-full group-hover:translate-x-full transition-transform duration-1000 ease-in-out pointer-events-none"
					></div>
					<div
						class="inline-block px-3 py-1 bg-[#141414]/10 text-[#141414] text-[10px] font-bold tracking-[0.2em] uppercase rounded-full mb-8 backdrop-blur-md border border-[#141414]/5"
					>
						Step 05
					</div>
					<h3 class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight">
						Conversation Launch & Daily Ops
					</h3>
					<p class="text-[#4A4A4F] text-lg leading-relaxed mb-10 font-normal max-w-2xl md:px-4">
						We launch focused, high-relevance campaigns and manage daily tasks. This means
						monitoring deliverability, adjusting volume, handling replies, and routing qualified
						leads directly to your calendar.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-8"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Campaign management
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Reply handling
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Lead routing
						</span>
					</div>
				</div>

				<!-- Step 06 -->
				<div
					data-step="6"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50px_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-out flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'6'
					)
						? 'opacity-100 translate-y-0 scale-100 blur-0'
						: 'opacity-0 translate-y-12 scale-[0.98] blur-[1px]'}"
				>
					<div
						class="absolute inset-0 bg-gradient-to-tr from-transparent via-white/20 to-transparent -translate-x-full group-hover:translate-x-full transition-transform duration-1000 ease-in-out pointer-events-none"
					></div>
					<div
						class="inline-block px-3 py-1 bg-[#141414]/10 text-[#141414] text-[10px] font-bold tracking-[0.2em] uppercase rounded-full mb-8 backdrop-blur-md border border-[#141414]/5"
					>
						Step 06
					</div>
					<h3 class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight">
						Optimization & Proof Reporting
					</h3>
					<p class="text-[#4A4A4F] text-lg leading-relaxed mb-10 font-normal max-w-2xl md:px-4">
						Cold email is about testing. We review performance weekly, find what works, and iterate
						systematically: subject lines, targeting, angles, and sequences.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-8"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Weekly performance reporting
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Iteration plan based on data
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold hover:border-[#141414]/30 hover:scale-105 hover:-translate-y-0.5 active:scale-95 transition-all duration-300"
						>
							Scale-up strategy
						</span>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 3: FINAL CTA -->
	<section class="pt-2 pb-24 md:pt-4 md:pb-32 bg-white relative">
		<div class="container mx-auto px-6">
			<div
				id="final-cta"
				class="max-w-6xl mx-auto transition-[opacity,transform] duration-1000 ease-[cubic-bezier(0.16,1,0.3,1)] flex flex-col items-center {finalCTAVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<!-- Risk-Free Badge Above -->
				<div
					class="flex items-center gap-2 px-4 py-1.5 rounded-full bg-[#141414] border border-white/10 mb-10 shadow-lg transition-transform hover:scale-105 duration-300"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="14"
						height="14"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="3"
						stroke-linecap="round"
						stroke-linejoin="round"
						class="text-white opacity-80"
						><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" /></svg
					>
					<span class="text-[10px] font-bold text-white tracking-[0.2em] uppercase"
						>Risk-Free Partnership</span
					>
				</div>

				<div
					class="w-full relative group p-16 md:p-28 rounded-[24px] bg-[#141414] border border-[#262626] shadow-[0_40px_100px_rgba(0,0,0,0.15)] overflow-hidden"
				>
					<!-- Solid Background Texture -->
					<div class="absolute inset-0 bg-card-grid opacity-60"></div>
					<div
						class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-[1px] bg-gradient-to-r from-transparent via-white/10 to-transparent"
					></div>

					<div class="relative z-10 flex flex-col items-center text-center">
						<h2
							class="text-2xl md:text-[40px] font-bold tracking-tight mb-10 leading-[1.2] md:leading-[1.15] text-gradient-metallic-dark max-w-[800px] transition-[opacity,transform] duration-1000 delay-100 {finalCTAVisible
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-8'}"
						>
							If you want more leads without hiring or guessing, this is it.
						</h2>

						<!-- CTA Section -->
						<div
							class="flex flex-col items-center gap-12 transition-[opacity,transform] duration-1000 delay-300 {finalCTAVisible
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-8'}"
						>
							<Button
								href="https://calendly.com/eastlineconsulting/30min"
								target="_blank"
								class="h-14 px-10 text-[16px] font-medium rounded-full bg-white/10 border border-white/25 text-white hover:bg-white/15 hover:shadow-[0_0_20px_rgba(255,255,255,0.1)] transition-[background-color,box-shadow,transform,border-color] duration-300 backdrop-blur-sm animate-shine group"
							>
								<span class="relative z-10 flex items-center gap-2 font-semibold">
									Get your 15 prospects
									<svg
										xmlns="http://www.w3.org/2000/svg"
										width="18"
										height="18"
										viewBox="0 0 24 24"
										fill="none"
										stroke="currentColor"
										stroke-width="3"
										stroke-linecap="round"
										stroke-linejoin="round"
										class="transition-transform group-hover:translate-x-1"
										><path d="M5 12h14" /><path d="m12 5 7 7-7 7" /></svg
									>
								</span>
							</Button>

							<!-- Guarantee Text -->
							<div
								class="flex flex-col items-center gap-6 w-full transition-[opacity,transform] duration-1000 delay-500 {finalCTAVisible
									? 'opacity-100 translate-y-0'
									: 'opacity-0 translate-y-8'}"
							>
								<p
									class="text-[#8F8F8F] text-sm md:text-base font-light tracking-wide max-w-2xl px-4"
								>
									<span
										class="text-white font-medium uppercase tracking-wider text-xs block mb-2 border-b border-white/20 pb-1 w-fit mx-auto"
										>The Results Guarantee</span
									>
									15 qualified prospects in your inbox in 60 days or less, or you get a full refund.
								</p>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>
</div>
