<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { onMount } from 'svelte';
	import { slide } from 'svelte/transition';

	let heroVisible = false;
	let trustStripVisible = false;
	let frameworkVisible = false;
	let offerVisible = false;
	let pillar1Visible = false;
	let pillar2Visible = false;
	let pillar3Visible = false;
	let savingsVisible = false;
	let modularVisible = false;
	let founderVisible = false;
	let finalCTAVisible = false;
	let activeFaq: number | null = null;

	onMount(() => {
		const observerOptions = {
			threshold: 0.1
		};

		const observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					const id = entry.target.id;
					if (id === 'hero-content') heroVisible = true;
					if (id === 'trust-strip') trustStripVisible = true;
					if (id === 'framework') frameworkVisible = true;
					if (id === 'pillar-1') pillar1Visible = true;
					if (id === 'pillar-2') pillar2Visible = true;
					if (id === 'pillar-3') pillar3Visible = true;
					if (id === 'savings') savingsVisible = true;
					if (id === 'modular') modularVisible = true;
					if (id === 'founder') founderVisible = true;
					if (id === 'final-cta') finalCTAVisible = true;
				}
			});
		}, observerOptions);

		const sections = [
			'hero-content',
			'trust-strip',
			'framework',
			'pillar-1',
			'pillar-2',
			'pillar-3',
			'founder',
			'final-cta'
		];

		sections.forEach((id) => {
			const el = document.getElementById(id);
			if (el) observer.observe(el);
		});

		return () => observer.disconnect();
	});

	function scrollToSection(id: string) {
		document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' });
	}
</script>

<svelte:head>
	<title>The B2B Growth Print Playbook | EastLine Consulting</title>
	<meta
		name="description"
		content="Get 30 qualified demos in 60 days or you don't pay. Architected by Mijo Majic. Proven B2B SaaS growth systems."
	/>
</svelte:head>

<div class="flex flex-col min-h-screen bg-white font-sans text-foreground selection:bg-primary/10">
	<!-- FLOATING NAVBAR -->
	<nav class="fixed top-4 left-1/2 -translate-x-1/2 z-50 w-[calc(100%-2rem)] max-w-5xl">
		<div
			class="flex items-center justify-between pl-8 pr-2 py-2 rounded-full bg-[#141414]/90 backdrop-blur-lg border border-[#333] shadow-[0_4px_20px_rgba(0,0,0,0.2)]"
		>
			<a href="/" class="flex items-center gap-2">
				<img
					src="/logo/EASTLINE CONSULTING.svg"
					alt="Eastline Consulting"
					class="h-6 w-auto brightness-0 invert"
				/>
			</a>
			<div class="hidden md:flex items-center gap-6">
				<button
					onclick={() => scrollToSection('pillar-1')}
					class="text-white/60 hover:text-white text-sm font-medium transition-colors cursor-pointer"
					>How It Works</button
				>
				<button
					onclick={() => scrollToSection('founder')}
					class="text-white/60 hover:text-white text-sm font-medium transition-colors cursor-pointer"
					>About</button
				>
				<a
					href="https://www.linkedin.com/in/mijomajic/"
					target="_blank"
					class="text-white/60 hover:text-white text-sm font-medium transition-colors cursor-pointer"
					>LinkedIn</a
				>
			</div>
			<Button
				href="/apply"
				target="_blank"
				class="h-10 px-5 text-sm font-semibold rounded-full bg-white text-[#141414] hover:bg-gray-200 transition-colors cursor-pointer"
			>
				Apply now
			</Button>
		</div>
	</nav>
	<!-- SECTION 1: HERO -->
	<section
		class="relative pt-24 pb-16 md:pt-40 lg:pt-48 md:pb-32 overflow-hidden bg-hero-gradient min-h-screen flex flex-col justify-center"
	>
		<div
			id="hero-content"
			class="container mx-auto px-6 md:px-4 text-center relative z-10 transition-[opacity,transform] duration-1000 ease-out {heroVisible
				? 'opacity-100 translate-y-0'
				: 'opacity-0 translate-y-8'}"
		>
			<!-- Eyebrow -->
			<div
				class="flex items-center justify-center gap-2 mb-8 delay-100 duration-1000 transition-[opacity,transform] {heroVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<div class="px-4 py-1.5 rounded-full bg-white/5 border border-white/10 backdrop-blur-sm">
					<span
						class="text-[11px] md:text-[12px] font-medium uppercase tracking-[0.2em] text-white/70"
					>
						For B2B SaaS
					</span>
				</div>
			</div>

			<!-- Headline -->
			<h1
				class="text-[28px] min-[390px]:text-[32px] md:text-5xl lg:text-[56px] font-bold tracking-tight mb-6 md:mb-8 leading-[1.15] md:leading-[1.1] max-w-5xl mx-auto px-2 md:px-0 [text-wrap:balance] delay-300 duration-1000 transition-[opacity,transform,filter] {heroVisible
					? 'opacity-100 translate-y-0 blur-0'
					: 'opacity-0 translate-y-8 blur-[10px]'}"
			>
				<span class="text-gradient-metallic-dark">
					30 qualified demos in 60 days or you don't pay
				</span>
			</h1>

			<!-- Subheadline -->
			<p
				class="text-base md:text-xl text-[#8F8F8F] max-w-[750px] mx-auto mb-12 md:mb-16 leading-relaxed font-light px-2 md:px-0 [text-wrap:balance] delay-500 duration-1000 transition-[opacity,transform,filter] {heroVisible
					? 'opacity-100 translate-y-0 blur-0'
					: 'opacity-0 translate-y-8 blur-[5px]'}"
			>
				We design and implement a complete B2B SaaS growth engine across acquisition, conversion,
				and retention.
			</p>

			<!-- Supporting Bullets -->
			<div
				class="flex flex-col md:flex-row items-center justify-center gap-4 md:gap-8 mb-10 md:mb-12 delay-600 duration-1000 transition-[opacity,transform] {heroVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<div class="flex items-center gap-2 text-white/60 text-sm">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="16"
						height="16"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"><path d="M20 6 9 17l-5-5" /></svg
					>
					<span>5000+ Leads generated</span>
				</div>
				<div class="flex items-center gap-2 text-white/60 text-sm">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="16"
						height="16"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"><path d="M20 6 9 17l-5-5" /></svg
					>
					<span>50+ Projects completed</span>
				</div>
				<div class="flex items-center gap-2 text-white/60 text-sm">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="16"
						height="16"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"><path d="M20 6 9 17l-5-5" /></svg
					>
					<span>3+ years as a CMO</span>
				</div>
			</div>

			<!-- CTAs -->
			<div
				class="flex flex-col sm:flex-row items-center justify-center gap-4 mb-12 md:mb-20 delay-700 duration-1000 transition-[opacity,transform] {heroVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<Button
					href="/apply"
					target="_blank"
					class="h-14 px-10 text-[15px] font-semibold rounded-full bg-white text-[#141414] hover:bg-white/90 hover:shadow-[0_0_30px_rgba(255,255,255,0.2)] transition-all duration-300 cursor-pointer"
				>
					Apply now
				</Button>
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

	<!-- SECTION 2: TRUST STRIP -->
	<section class="py-16 bg-white border-b border-[#F0F0F0]">
		<div
			id="trust-strip"
			class="container mx-auto px-6 md:px-4 transition-[opacity,transform] duration-700 ease-out {trustStripVisible
				? 'opacity-100 translate-y-0'
				: 'opacity-0 translate-y-6'}"
		>
			<div class="grid grid-cols-2 md:grid-cols-4 gap-8 md:gap-12 max-w-5xl mx-auto">
				<div class="text-center">
					<p class="text-[11px] font-bold tracking-[0.15em] uppercase text-[#8F8F8F] mb-2">
						Covers
					</p>
					<p class="text-[#141414] font-semibold text-sm">Email, SEO, CRO, and more</p>
				</div>
				<div class="text-center">
					<p class="text-[11px] font-bold tracking-[0.15em] uppercase text-[#8F8F8F] mb-2">
						Includes
					</p>
					<p class="text-[#141414] font-semibold text-sm">Strategy + DFY</p>
				</div>
				<div class="text-center">
					<p class="text-[11px] font-bold tracking-[0.15em] uppercase text-[#8F8F8F] mb-2">
						Replaces
					</p>
					<p class="text-[#141414] font-semibold text-sm">$300K+/year in hires</p>
				</div>
				<div class="text-center">
					<p class="text-[11px] font-bold tracking-[0.15em] uppercase text-[#8F8F8F] mb-2">
						Timeline
					</p>
					<p class="text-[#141414] font-semibold text-sm">8 weeks, no lock-in</p>
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 3: THE CORE FRAMEWORK -->
	<section class="pt-24 md:pt-32 pb-16 md:pb-24 bg-white">
		<div class="container mx-auto px-6 md:px-4 max-w-5xl">
			<div
				id="framework"
				class="text-center transition-[opacity,transform] duration-700 ease-out {frameworkVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-6'}"
			>
				<h2
					class="text-3xl md:text-5xl font-bold tracking-tight mb-6 text-[#141414] overflow-hidden"
				>
					<span
						class="inline-block transition-all duration-1000 ease-[cubic-bezier(0.16,1,0.3,1)] delay-[0ms] {frameworkVisible
							? 'opacity-100 translate-y-0'
							: 'opacity-0 translate-y-full'}">Acquisition.</span
					>
					<span
						class="inline-block transition-all duration-1000 ease-[cubic-bezier(0.16,1,0.3,1)] delay-[150ms] {frameworkVisible
							? 'opacity-100 translate-y-0'
							: 'opacity-0 translate-y-full'}">Conversion.</span
					>
					<span
						class="inline-block transition-all duration-1000 ease-[cubic-bezier(0.16,1,0.3,1)] delay-[300ms] {frameworkVisible
							? 'opacity-100 translate-y-0'
							: 'opacity-0 translate-y-full'}">Retention.</span
					>
				</h2>
				<p class="text-[#8F8F8F] text-lg font-light max-w-2xl mx-auto leading-relaxed">
					Most SaaS teams grow slowly because these systems are built in isolation. We install all
					three as one integrated engine.
				</p>
			</div>
		</div>
	</section>

	<!-- SECTION 5: PILLAR 1 — STRATEGY & DIAGNOSIS -->
	<section class="pt-16 md:pt-24 pb-16 md:pb-24 bg-white">
		<div class="container mx-auto px-6 md:px-4 max-w-5xl">
			<div
				id="pillar-1"
				class="transition-[opacity,transform] duration-700 ease-out {pillar1Visible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-6'}"
			>
				<div class="flex items-center gap-3 mb-4">
					<span
						class="px-3 py-1 rounded-full bg-[#141414] text-white text-[10px] font-bold tracking-[0.15em] uppercase"
						>Pillar 1</span
					>
					<span class="text-[#8F8F8F] text-sm">Foundation</span>
				</div>
				<div class="flex items-center gap-3 mb-4">
					<div class="p-2 rounded-lg bg-black text-white">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							width="20"
							height="20"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							><path d="M21.21 15.89A10 10 0 1 1 8 2.83" /><path
								d="M22 12A10 10 0 0 0 12 2v10z"
							/></svg
						>
					</div>
					<h2 class="text-3xl md:text-4xl font-bold tracking-tight text-[#141414]">
						Strategy & Diagnosis
					</h2>
				</div>
				<p class="text-[#8F8F8F] text-lg font-light mb-12 max-w-2xl">
					Define <em>who</em> you grow, <em>why</em> they buy, and <em>where</em> growth is leaking.
				</p>

				<div class="grid md:grid-cols-2 gap-8">
					<div class="p-8 rounded-2xl bg-[#FAFAFA] border border-[#EBEBEB]">
						<h3 class="text-lg font-bold text-[#141414] mb-6">Deliverables</h3>
						<ul class="space-y-3 text-[#4A4A4F]">
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>ICP definition & segmentation</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Jobs-to-be-done mapping</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Value proposition refinement</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Messaging framework (headlines, CTAs, angles)</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Competitive teardown</span>
							</li>
						</ul>
					</div>

					<div class="p-8 rounded-2xl bg-[#FAFAFA] border border-[#EBEBEB]">
						<h3 class="text-lg font-bold text-[#141414] mb-6">Audit & Tracking</h3>
						<ul class="space-y-3 text-[#4A4A4F]">
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Full funnel audit</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Conversion bottleneck map</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Event tracking plan</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Growth dashboard blueprint</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-2"></span>
								<span>Prioritized opportunity backlog</span>
							</li>
						</ul>
					</div>
				</div>

				<div class="mt-8 p-6 rounded-xl bg-[#141414] text-white">
					<p class="text-sm font-medium">
						<strong>Outcome:</strong> A single source of truth for every growth decision.
					</p>
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 6: PILLAR 2 — ACQUISITION SYSTEMS -->
	<section class="py-16 md:py-24 bg-[#FAFAFA] border-y border-[#EBEBEB]">
		<div class="container mx-auto px-6 md:px-4 max-w-5xl">
			<div
				id="pillar-2"
				class="transition-[opacity,transform] duration-700 ease-out {pillar2Visible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-6'}"
			>
				<div class="flex items-center gap-3 mb-4">
					<span
						class="px-3 py-1 rounded-full bg-[#141414] text-white text-[10px] font-bold tracking-[0.15em] uppercase"
						>Pillar 2</span
					>
					<span class="text-[#8F8F8F] text-sm">Demand</span>
				</div>
				<div class="flex items-center gap-3 mb-4">
					<div class="p-2 rounded-lg bg-black text-white">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							width="20"
							height="20"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2" /><circle
								cx="9"
								cy="7"
								r="4"
							/><path d="M22 21v-2a4 4 0 0 0-3-3.87" /><path d="M16 3.13a4 4 0 0 1 0 7.75" /></svg
						>
					</div>
					<h2 class="text-3xl md:text-4xl font-bold tracking-tight text-[#141414]">
						Acquisition Systems
					</h2>
				</div>
				<p class="text-[#8F8F8F] text-lg font-light mb-12 max-w-2xl">
					Build repeatable engines that generate qualified demand at scale.
				</p>

				<div class="space-y-8">
					<!-- Outbound Engine -->
					<div class="p-8 rounded-2xl bg-white border border-[#E5E5E5] shadow-sm">
						<div class="flex flex-col md:flex-row md:items-start md:justify-between gap-4 mb-6">
							<div>
								<h3 class="text-xl font-bold text-[#141414] mb-1">A. Outbound Engine</h3>
								<p class="text-sm text-[#8F8F8F]">Cold Email + LinkedIn</p>
							</div>
							<span
								class="px-3 py-1 rounded-full bg-[#141414] text-white text-xs font-medium whitespace-nowrap"
							>
								Replaces: SDRs, outbound manager, RevOps
							</span>
						</div>
						<div class="grid sm:grid-cols-2 gap-3">
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Scalable cold email architecture</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>ICP-based lead lists</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Conversion-focused copy + follow-ups</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Reply → booked call logic</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>LinkedIn outbound scripts & flows</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Deliverability setup</span>
							</div>
						</div>
					</div>

					<!-- Inbound & Lead Magnets -->
					<div class="p-8 rounded-2xl bg-white border border-[#E5E5E5] shadow-sm">
						<div class="flex flex-col md:flex-row md:items-start md:justify-between gap-4 mb-6">
							<div>
								<h3 class="text-xl font-bold text-[#141414] mb-1">B. Inbound & Lead Magnets</h3>
								<p class="text-sm text-[#8F8F8F]">Content assets that convert</p>
							</div>
							<span
								class="px-3 py-1 rounded-full bg-[#141414] text-white text-xs font-medium whitespace-nowrap"
							>
								Replaces: Content strategist + growth marketer
							</span>
						</div>
						<div class="grid sm:grid-cols-2 gap-3">
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Lead magnet strategy</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Free tools & calculators</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Resource hubs (templates, playbooks)</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>YouTube content angle maps</span>
							</div>
						</div>
					</div>

					<!-- SEO & Organic -->
					<div class="p-8 rounded-2xl bg-white border border-[#E5E5E5] shadow-sm">
						<div class="flex flex-col md:flex-row md:items-start md:justify-between gap-4 mb-6">
							<div>
								<h3 class="text-xl font-bold text-[#141414] mb-1">C. Organic Demand & SEO</h3>
								<p class="text-sm text-[#8F8F8F]">Including AI Discovery (GEO)</p>
							</div>
							<span
								class="px-3 py-1 rounded-full bg-[#141414] text-white text-xs font-medium whitespace-nowrap"
							>
								Replaces: SEO lead + content ops
							</span>
						</div>
						<div class="grid sm:grid-cols-2 gap-3">
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>SaaS-specific SEO growth model</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Search intent & keyword segmentation</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Use case & comparison pages</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Programmatic SEO opportunities</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>Technical SEO & indexing audit</span>
							</div>
							<div class="flex items-center gap-2 text-[#4A4A4F] text-sm">
								<span class="w-1 h-1 rounded-full bg-[#141414]"></span>
								<span>GEO playbook & AI discovery</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 7: PILLAR 3 — CONVERSION & REVENUE -->
	<section class="py-16 md:py-24 bg-white">
		<div class="container mx-auto px-6 md:px-4 max-w-5xl">
			<div
				id="pillar-3"
				class="transition-[opacity,transform] duration-700 ease-out {pillar3Visible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-6'}"
			>
				<div class="flex items-center gap-3 mb-4">
					<span
						class="px-3 py-1 rounded-full bg-[#141414] text-white text-[10px] font-bold tracking-[0.15em] uppercase"
						>Pillar 3</span
					>
					<span class="text-[#8F8F8F] text-sm">Revenue</span>
				</div>
				<div class="flex items-center gap-3 mb-4">
					<div class="p-2 rounded-lg bg-black text-white">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							width="20"
							height="20"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							><path d="M12 2v20" /><path
								d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"
							/></svg
						>
					</div>
					<h2 class="text-3xl md:text-4xl font-bold tracking-tight text-[#141414]">
						Conversion & Revenue Systems
					</h2>
				</div>
				<p class="text-[#8F8F8F] text-lg font-light mb-12 max-w-2xl">
					Turn trials into customers and customers into advocates.
				</p>

				<div class="grid md:grid-cols-2 gap-8">
					<!-- CRO -->
					<div class="p-8 rounded-2xl bg-[#FAFAFA] border border-[#EBEBEB]">
						<div class="mb-6">
							<h3 class="text-xl font-bold text-[#141414] mb-1">
								Product-Led Conversion Optimization
							</h3>
							<span class="text-xs text-white bg-[#141414] px-2 py-0.5 rounded-full"
								>Replaces: CRO specialist + product marketing</span
							>
						</div>
						<ul class="space-y-3 text-[#4A4A4F] text-sm">
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Trial & signup teardown</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Activation event definition</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Time-to-value reduction plan</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Onboarding UX & in-app copy</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Behavioral segmentation</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Experiment & priority roadmap</span>
							</li>
						</ul>
					</div>

					<!-- Lifecycle -->
					<div class="p-8 rounded-2xl bg-[#FAFAFA] border border-[#EBEBEB]">
						<div class="mb-6">
							<h3 class="text-xl font-bold text-[#141414] mb-1">Lifecycle Email & SMS Systems</h3>
							<span class="text-xs text-white bg-[#141414] px-2 py-0.5 rounded-full"
								>Replaces: Email marketer + lifecycle manager</span
							>
						</div>
						<ul class="space-y-3 text-[#4A4A4F] text-sm">
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Trial & activation sequences</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Objection-handling flows</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Abandoned signup recovery</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Founder-led brand emails</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Feature launches & newsletters</span>
							</li>
							<li class="flex items-start gap-3">
								<span class="w-1.5 h-1.5 rounded-full bg-[#141414] mt-1.5"></span>
								<span>Re-engagement, win-back & SMS nudges</span>
							</li>
						</ul>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 10: FOUNDER SECTION -->
	<section class="py-24 md:py-32 bg-[#FAFAFA] border-y border-[#EBEBEB]">
		<div class="container mx-auto px-6 md:px-4 max-w-5xl">
			<div
				id="founder"
				class="transition-[opacity,transform] duration-700 ease-out {founderVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-6'}"
			>
				<!-- Main bio section -->
				<div class="flex flex-col md:flex-row gap-12 md:gap-16 items-center md:items-start mb-16">
					<!-- Photo & Social -->
					<div class="flex-shrink-0 flex flex-col items-center md:items-stretch gap-4">
						<div
							class="w-48 h-48 md:w-64 md:h-64 rounded-2xl bg-[#141414] border border-[#333] shadow-[0_20px_50px_rgba(0,0,0,0.2)] overflow-hidden"
						>
							<img src="/images/mijo.png" alt="Mijo Majic" class="w-full h-full object-cover" />
						</div>
						<a
							href="https://www.linkedin.com/in/mijomajic/"
							target="_blank"
							class="w-48 md:w-full flex items-center justify-center gap-2 p-3 rounded-xl bg-[#141414] text-white hover:bg-black transition-colors"
							aria-label="LinkedIn"
						>
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="16"
								height="16"
								viewBox="0 0 24 24"
								fill="currentColor"
							>
								<path
									d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
								/>
							</svg>
							<span class="text-xs font-bold uppercase tracking-wider">Connect on LinkedIn</span>
						</a>
					</div>
					<!-- Text content -->
					<div class="flex-1 text-center md:text-left">
						<p class="text-[11px] font-bold tracking-[0.15em] uppercase text-[#8F8F8F] mb-2">
							Growth marketer & System Architect
						</p>
						<h2 class="text-3xl md:text-5xl font-bold tracking-tight mb-6 text-[#141414]">
							Mijo Majic
						</h2>
						<div class="space-y-4 text-[#4A4A4F] text-base leading-relaxed mb-6">
							<p>
								Every project at EastLine is architected and managed by me. With a background in B2B
								SaaS Acquisition that made my clients $250k+ through just email, I ensure that the
								systems' output meets the standards of a senior growth team.
							</p>
						</div>
						<!-- Stats & Social -->
						<div class="grid grid-cols-2 sm:grid-cols-3 gap-y-6 gap-x-8 mb-10">
							<div>
								<p class="text-xl font-bold text-[#141414] leading-none mb-1">5000+</p>
								<p class="text-[10px] uppercase tracking-wider text-[#8F8F8F] font-semibold">
									Leads generated
								</p>
							</div>
							<div>
								<p class="text-xl font-bold text-[#141414] leading-none mb-1">50+</p>
								<p class="text-[10px] uppercase tracking-wider text-[#8F8F8F] font-semibold">
									Projects completed
								</p>
							</div>
							<div>
								<p class="text-xl font-bold text-[#141414] leading-none mb-1">$250k</p>
								<p class="text-[10px] uppercase tracking-wider text-[#8F8F8F] font-semibold">
									Pipeline generated
								</p>
							</div>
							<div>
								<p class="text-xl font-bold text-[#141414] leading-none mb-1">#1</p>
								<p class="text-[10px] uppercase tracking-wider text-[#8F8F8F] font-semibold">
									Page growth in country
								</p>
							</div>
							<div>
								<p class="text-xl font-bold text-[#141414] leading-none mb-1">Expert</p>
								<p class="text-[10px] uppercase tracking-wider text-[#8F8F8F] font-semibold">
									CMO experience
								</p>
							</div>
							<div>
								<p class="text-xl font-bold text-[#141414] leading-none mb-1">10M+</p>
								<p class="text-[10px] uppercase tracking-wider text-[#8F8F8F] font-semibold">
									Organic views generated
								</p>
							</div>
						</div>
					</div>
				</div>

				<!-- Trust strip cards -->
				<div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-4">
					<div class="p-6 rounded-xl bg-white border border-[#E5E5E5]">
						<div class="w-10 h-10 rounded-lg bg-[#141414] flex items-center justify-center mb-4">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="20"
								height="20"
								viewBox="0 0 24 24"
								fill="none"
								stroke="white"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"
								><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z" /></svg
							>
						</div>
						<h4 class="font-bold text-[#141414] mb-1">Direct Access</h4>
						<p class="text-[#8F8F8F] text-sm">
							You communicate directly with me, the person actually building your system.
						</p>
					</div>
					<div class="p-6 rounded-xl bg-white border border-[#E5E5E5]">
						<div class="w-10 h-10 rounded-lg bg-[#141414] flex items-center justify-center mb-4">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="20"
								height="20"
								viewBox="0 0 24 24"
								fill="none"
								stroke="white"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"
								><path d="M12 20h9" /><path
									d="M16.5 3.5a2.121 2.121 0 0 1 3 3L7 19l-4 1 1-4L16.5 3.5z"
								/></svg
							>
						</div>
						<h4 class="font-bold text-[#141414] mb-1">Senior Decisions</h4>
						<p class="text-[#8F8F8F] text-sm">
							Decisions made by someone with years of experience, not delegated to juniors.
						</p>
					</div>
					<div class="p-6 rounded-xl bg-white border border-[#E5E5E5]">
						<div class="w-10 h-10 rounded-lg bg-[#141414] flex items-center justify-center mb-4">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="20"
								height="20"
								viewBox="0 0 24 24"
								fill="none"
								stroke="white"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"
								><path
									d="M12 22c5.523 0 10-4.477 10-10S17.523 2 12 2 2 6.477 2 12s4.477 10 10 10z"
								/><path d="m9 12 2 2 4-4" /></svg
							>
						</div>
						<h4 class="font-bold text-[#141414] mb-1">Full Ownership</h4>
						<p class="text-[#8F8F8F] text-sm">
							One person accountable for the entire project. No finger-pointing.
						</p>
					</div>
					<div class="p-6 rounded-xl bg-white border border-[#E5E5E5]">
						<div class="w-10 h-10 rounded-lg bg-[#141414] flex items-center justify-center mb-4">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="20"
								height="20"
								viewBox="0 0 24 24"
								fill="none"
								stroke="white"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"
								><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z" /><polyline
									points="14 2 14 8 20 8"
								/><line x1="16" y1="13" x2="8" y2="13" /><line
									x1="16"
									y1="17"
									x2="8"
									y2="17"
								/><polyline points="10 9 9 9 8 9" /></svg
							>
						</div>
						<h4 class="font-bold text-[#141414] mb-1">Clear Communication</h4>
						<p class="text-[#8F8F8F] text-sm">
							Weekly updates, clear documentation, and honest timelines. No surprises.
						</p>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 11: FINAL CTA -->
	<section class="py-24 md:py-32 bg-white">
		<div class="container mx-auto px-6">
			<div
				id="final-cta"
				class="max-w-5xl mx-auto transition-[opacity,transform] duration-700 ease-out flex flex-col items-center {finalCTAVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-6'}"
			>
				<div
					class="w-full relative p-12 md:p-20 rounded-[24px] bg-[#141414] border border-[#262626] overflow-hidden"
				>
					<div class="absolute inset-0 bg-card-grid opacity-60"></div>
					<div
						class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-[1px] bg-gradient-to-r from-transparent via-white/10 to-transparent"
					></div>

					<div class="relative z-10 flex flex-col items-center text-center">
						<h2
							class="text-2xl md:text-4xl font-bold tracking-tight mb-8 leading-[1.2] text-gradient-metallic-dark max-w-[700px]"
						>
							If your product works, your growth system shouldn't be the bottleneck.
						</h2>

						<div class="flex flex-col sm:flex-row items-center gap-4 mb-8">
							<Button
								href="/apply"
								target="_blank"
								class="h-14 px-10 text-[15px] font-semibold rounded-full bg-white text-[#141414] hover:bg-white/90 hover:shadow-[0_0_30px_rgba(255,255,255,0.2)] transition-all duration-300 pointer-events-auto cursor-pointer"
							>
								Apply now
							</Button>
						</div>

						<p class="text-[#8F8F8F] text-sm">
							8-week implementation · No long-term lock-in · Zero Risk
						</p>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 12: FOOTER -->
	<footer class="py-12 bg-[#141414] border-t border-[#262626]">
		<div class="container mx-auto px-6 md:px-4 max-w-5xl">
			<div class="flex flex-col md:flex-row md:items-center md:justify-between gap-8">
				<div>
					<p class="text-white/40 text-sm mb-2">
						<span class="text-white/60 font-medium">For:</span> B2B SaaS
					</p>
				</div>
				<div class="flex items-center gap-6">
					<img
						src="/logo/EASTLINE CONSULTING.svg"
						alt="Eastline Consulting"
						class="h-6 w-auto brightness-0 invert opacity-40 hover:opacity-100 transition-opacity"
					/>
					<a
						href="mailto:hello@eastlineconsulting.com"
						class="text-white/40 hover:text-white/70 text-sm transition-colors"
					>
						Contact
					</a>
					<a href="/privacy" class="text-white/40 hover:text-white/70 text-sm transition-colors">
						Privacy
					</a>
					<a
						href="https://www.linkedin.com/in/mijomajic/"
						target="_blank"
						aria-label="LinkedIn"
						class="text-white/40 hover:text-white/70 transition-colors"
					>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							width="18"
							height="18"
							viewBox="0 0 24 24"
							fill="currentColor"
						>
							<path
								d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
							/>
						</svg>
					</a>
				</div>
			</div>
			<div class="mt-8 pt-8 border-t border-white/10 text-center">
				<p class="text-white/30 text-xs">© 2026 Eastline Consulting. All rights reserved.</p>
			</div>
		</div>
	</footer>
</div>
