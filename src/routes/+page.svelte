<script lang="ts">
	import { Button } from "$lib/components/ui/button";
	import { Star } from "@lucide/svelte";
	import { onMount } from "svelte";
	import { slide } from "svelte/transition";

	let visibleSteps = new Set();
	let heroVisible = false;
	let processHeaderVisible = false;
	let activeFaq: number | null = null;
	let faqVisible = false;
	let finalCTAVisible = false;

	onMount(() => {
		const observerOptions = {
			threshold: 0.1,
		};

		const observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					if (entry.target.id === "hero-content") heroVisible = true;
					if (entry.target.id === "process-header")
						processHeaderVisible = true;
					if (entry.target.id === "faq") faqVisible = true;
					if (entry.target.id === "final-cta") finalCTAVisible = true;
					if (
						entry.target instanceof HTMLElement &&
						entry.target.dataset.step
					) {
						visibleSteps.add(entry.target.dataset.step);
						visibleSteps = visibleSteps; // trigger reactivity
					}
				}
			});
		}, observerOptions);

		const hero = document.getElementById("hero-content");
		const processHeader = document.getElementById("process-header");
		const faq = document.getElementById("faq");
		const finalCta = document.getElementById("final-cta");
		const steps = document.querySelectorAll("[data-step]");

		if (hero) observer.observe(hero);
		if (processHeader) observer.observe(processHeader);
		if (faq) observer.observe(faq);
		if (finalCta) observer.observe(finalCta);
		steps.forEach((step) => observer.observe(step));

		return () => observer.disconnect();
	});
</script>

<svelte:head>
	<title
		>DFY Cold Email for Virtual Staging - 15 Realtor Calls in 90 Days |
		Eastline Consulting</title
	>
</svelte:head>

<div
	class="flex flex-col min-h-screen bg-white font-sans text-foreground selection:bg-primary/10"
>
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
					>DFY cold email for virtual staging companies that books 15
					qualified realtor calls in 90 days guaranteed.</span
				>
			</h1>

			<!-- Subheadline -->
			<p
				class="text-base md:text-xl text-[#8F8F8F] max-w-[700px] mx-auto mb-10 md:mb-12 leading-relaxed font-light px-2 md:px-0 [text-wrap:balance] delay-500 duration-1000 transition-[opacity,transform,filter] {heroVisible
					? 'opacity-100 translate-y-0 blur-0'
					: 'opacity-0 translate-y-8 blur-[5px]'}"
			>
				We use high-volume cold email + direct-response messaging to put
				real estate agent conversations on your calendar or we work for
				free.
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
					Book 15 realtor calls
				</Button>
				<p class="mt-3 md:mt-4 text-sm text-[#8F8F8F] font-light">
					See if you qualify.
				</p>
			</div>
		</div>

		<div
			class="absolute bottom-8 md:bottom-10 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 md:gap-3 delay-[1200ms] duration-1000 transition-[opacity,transform] {heroVisible
				? 'opacity-100 translate-y-0'
				: 'opacity-0 translate-y-4'}"
		>
			<div class="flex flex-col items-center gap-2">
				<span
					class="text-[10px] font-bold tracking-[0.2em] uppercase text-[#8F8F8F] mr-[-0.2em]"
				>
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
				class="text-center mb-12 transition-[opacity,transform] duration-1000 ease-out {processHeaderVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<h2
					class="text-3xl md:text-5xl font-bold tracking-tight mb-4 text-[#141414]"
				>
					The Entire Process
				</h2>
				<div class="max-w-lg mx-auto border-b border-[#EBEBEB] pb-8">
					<p
						class="text-[#8F8F8F] text-lg font-light leading-relaxed"
					>
						You’re paying for a full outbound engine: targeting,
						deliverability, sequencing, reply management, and
						tracking.
					</p>
				</div>
			</div>

			<div class="space-y-16">
				<!-- Step 01 -->
				<div
					data-step="1"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-[cubic-bezier(0.16,1,0.3,1)] flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'1',
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
					<h3
						class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight"
					>
						Market–Match Offer & Angle
					</h3>
					<p
						class="text-[#4A4A4F] text-lg leading-relaxed mb-12 font-normal max-w-2xl md:px-4"
					>
						Before we send anything, we lock the message for your
						exact offer that makes realtors care - the angle that
						gets <strong>replies</strong>, not “sounds good,” based
						on actual data and research.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-0"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[100ms] {visibleSteps.has(
								'1',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							ICP + buyer psychology
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[200ms] {visibleSteps.has(
								'1',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Offer positioning
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[300ms] {visibleSteps.has(
								'1',
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
						'2',
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
					<h3
						class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight"
					>
						Signal-Based Realtor Targeting
					</h3>
					<p
						class="text-[#4A4A4F] text-lg leading-relaxed mb-12 font-normal max-w-2xl md:px-4"
					>
						Generic lists get deleted. We build your prospect
						universe using role + relevance + buying signals, then
						segment so emails feel specific.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-0"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[100ms] {visibleSteps.has(
								'2',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Realtor datasets
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[200ms] {visibleSteps.has(
								'2',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Segmentation
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[300ms] {visibleSteps.has(
								'2',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Verification + anti-bounce
						</span>
					</div>
				</div>

				<!-- Step 03 -->
				<div
					data-step="3"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-out flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'3',
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
					<h3
						class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight"
					>
						Deliverability & Sending Infrastructure
					</h3>
					<p
						class="text-[#4A4A4F] text-lg leading-relaxed mb-12 font-normal max-w-2xl md:px-4"
					>
						If you’re not landing in the primary inbox, you’re
						invisible. We set up a sending system designed to stay
						healthy at scale and avoid ruining reputation.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-0"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[100ms] {visibleSteps.has(
								'3',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Multi-domain + Multi-inbox
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[200ms] {visibleSteps.has(
								'3',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							SPF / DKIM / DMARC
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[300ms] {visibleSteps.has(
								'3',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Warmup + Inbox Health
						</span>
					</div>
				</div>

				<!-- Step 05 -->
				<div
					data-step="5"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-out flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'5',
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
					<h3
						class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight"
					>
						Launch + Reply Flow
					</h3>
					<p
						class="text-[#4A4A4F] text-lg leading-relaxed mb-12 font-normal max-w-2xl md:px-4"
					>
						We handle daily ops on the outbound side: monitoring
						deliverability, managing volume and organizing leads.
						Then we install a <strong
							>Reply-to-Booking playbook</strong
						> your team follows to convert interested replies into scheduled
						calls.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-0"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[100ms] {visibleSteps.has(
								'5',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Outbound operations
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[200ms] {visibleSteps.has(
								'5',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Reply-to-Booking playbook
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[300ms] {visibleSteps.has(
								'5',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Lead routing
						</span>
					</div>
				</div>

				<!-- Step 06 -->
				<div
					data-step="6"
					class="relative group p-10 md:p-16 rounded-[24px] bg-gradient-to-br from-[#E2E2E2] via-[#F8F8F8] to-[#D1D1D1] border border-[#B8B8B8] shadow-[inset_0_1px_1px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_20px_50px_rgba(0,0,0,0.08)] hover:shadow-[inset_0_2px_2px_rgba(255,255,255,1),inset_0_-1px_1px_rgba(0,0,0,0.1),0_30px_60_rgba(0,0,0,0.12)] transition-[opacity,transform,filter] duration-1000 ease-out flex flex-col items-start md:items-center text-left md:text-center max-w-4xl mx-auto overflow-hidden {visibleSteps.has(
						'6',
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
					<h3
						class="text-2xl md:text-4xl font-bold mb-6 text-[#141414] tracking-tight"
					>
						Weekly Optimization & Proof Reporting
					</h3>
					<p
						class="text-[#4A4A4F] text-lg leading-relaxed mb-12 font-normal max-w-2xl md:px-4"
					>
						Weekly review + iteration: lists, segments, angles,
						subjects, and sequences - to increase reply quality and
						conversion. Weekly reports get sent straight to you.
					</p>
					<div
						class="flex flex-col md:flex-row items-start md:items-center md:justify-center gap-3 mt-0"
					>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[100ms] {visibleSteps.has(
								'6',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Weekly review + iteration
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[200ms] {visibleSteps.has(
								'6',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Reply quality optimization
						</span>
						<span
							class="px-5 py-2.5 rounded-full bg-[#F5F5F7]/80 backdrop-blur-sm border border-[#C8C8C8] shadow-[0_1px_2px_rgba(0,0,0,0.05)] text-sm text-[#141414] font-semibold transition-[opacity,transform] duration-700 delay-[300ms] {visibleSteps.has(
								'6',
							)
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-4'}"
						>
							Direct-to-you reports
						</span>
					</div>
				</div>
			</div>
		</div>
	</section>
	<!-- SECTION 3: FAQ -->
	<section class="pt-24 pb-16 bg-white border-t border-[#F5F5F7]">
		<div class="container mx-auto px-6 md:px-4 max-w-4xl">
			<div
				id="faq"
				class="text-center mb-16 transition-[opacity,transform] duration-500 ease-out {faqVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-8'}"
			>
				<h2
					class="text-3xl md:text-5xl font-bold tracking-tight mb-4 text-[#141414]"
				>
					FAQ
				</h2>
				<p class="text-[#8F8F8F] text-lg font-light max-w-lg mx-auto">
					Common questions about how we scale your realtor
					acquisition.
				</p>
			</div>

			<div class="space-y-6">
				<!-- FAQ 01 -->
				<div
					class="relative group rounded-[22px] bg-white border border-[#EBEBEB] shadow-[0_1px_3px_rgba(0,0,0,0.02),0_10px_40px_rgba(0,0,0,0.04)] transition-all duration-300 delay-[50ms] {faqVisible
						? 'opacity-100 translate-y-0'
						: 'opacity-0 translate-y-4'} overflow-hidden"
				>
					<button
						class="w-full px-6 py-5 text-left flex justify-between items-center group/btn"
						onclick={() => (activeFaq = activeFaq === 1 ? null : 1)}
					>
						<div class="flex items-center gap-4">
							<span
								class="text-[10px] font-bold tracking-[0.2em] text-[#A1A1A1] uppercase"
								>01</span
							>
							<span class="text-base font-bold text-[#141414]"
								>Do you book calls for us?</span
							>
						</div>
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
							class="text-[#8F8F8F] transition-transform duration-300 {activeFaq ===
							1
								? 'rotate-180'
								: ''}"><path d="m6 9 6 6 6-6" /></svg
						>
					</button>
					{#if activeFaq === 1}
						<div
							transition:slide={{ duration: 300 }}
							class="px-8 pb-8 pt-0"
						>
							<div
								class="h-[1px] w-full bg-[#141414]/5 mb-6"
							></div>
							<p
								class="text-[#4A4A4F] text-lg leading-relaxed max-w-3xl"
							>
								We build and manage the outbound infrastructure
								that generates qualified interest. We then
								provide the Reply to Booking playbook that your
								team uses to convert those active conversations
								into scheduled calls on your calendar.
							</p>
						</div>
					{/if}
				</div>

				<!-- FAQ 02 -->
				<div
					class="relative group rounded-[22px] bg-white border border-[#EBEBEB] shadow-[0_1px_3px_rgba(0,0,0,0.02),0_10px_40px_rgba(0,0,0,0.04)] transition-all duration-300 delay-100 {faqVisible
						? 'opacity-100 translate-y-0'
						: 'opacity-0 translate-y-4'} overflow-hidden"
				>
					<button
						class="w-full px-6 py-5 text-left flex justify-between items-center group/btn"
						onclick={() => (activeFaq = activeFaq === 2 ? null : 2)}
					>
						<div class="flex items-center gap-4">
							<span
								class="text-[10px] font-bold tracking-[0.2em] text-[#A1A1A1] uppercase"
								>02</span
							>
							<span class="text-base font-bold text-[#141414]"
								>How does the guarantee work?</span
							>
						</div>
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
							class="text-[#8F8F8F] transition-transform duration-300 {activeFaq ===
							2
								? 'rotate-180'
								: ''}"><path d="m6 9 6 6 6-6" /></svg
						>
					</button>
					{#if activeFaq === 2}
						<div
							transition:slide={{ duration: 300 }}
							class="px-8 pb-8 pt-0"
						>
							<div
								class="h-[1px] w-full bg-[#141414]/5 mb-6"
							></div>
							<p
								class="text-[#4A4A4F] text-lg leading-relaxed max-w-3xl"
							>
								If we do not hit the benchmark of 15 qualified
								calls in 90 days while you are following our
								operational protocols, we continue to manage
								your outbound systems for free until that target
								is reached.
							</p>
						</div>
					{/if}
				</div>

				<!-- FAQ 03 -->
				<div
					class="relative group rounded-[22px] bg-white border border-[#EBEBEB] shadow-[0_1px_3px_rgba(0,0,0,0.02),0_10px_40px_rgba(0,0,0,0.04)] transition-all duration-300 delay-[150ms] {faqVisible
						? 'opacity-100 translate-y-0'
						: 'opacity-0 translate-y-4'} overflow-hidden"
				>
					<button
						class="w-full px-6 py-5 text-left flex justify-between items-center group/btn"
						onclick={() => (activeFaq = activeFaq === 3 ? null : 3)}
					>
						<div class="flex items-center gap-4">
							<span
								class="text-[10px] font-bold tracking-[0.2em] text-[#A1A1A1] uppercase"
								>03</span
							>
							<span class="text-base font-bold text-[#141414]"
								>What counts as a qualified call?</span
							>
						</div>
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
							class="text-[#8F8F8F] transition-transform duration-300 {activeFaq ===
							3
								? 'rotate-180'
								: ''}"><path d="m6 9 6 6 6-6" /></svg
						>
					</button>
					{#if activeFaq === 3}
						<div
							transition:slide={{ duration: 300 }}
							class="px-8 pb-8 pt-0"
						>
							<div
								class="h-[1px] w-full bg-[#141414]/5 mb-6"
							></div>
							<p
								class="text-[#4A4A4F] text-lg leading-relaxed max-w-3xl"
							>
								A qualified call is defined by three criteria:
								the prospect matches our pre-agreed realtor or
								brokerage segment, they meet your specific
								qualification requirements, and they attend the
								scheduled meeting.
							</p>
						</div>
					{/if}
				</div>

				<!-- FAQ 04 -->
				<div
					class="relative group rounded-[22px] bg-white border border-[#EBEBEB] shadow-[0_1px_3px_rgba(0,0,0,0.02),0_10px_40px_rgba(0,0,0,0.04)] transition-all duration-300 delay-[200ms] {faqVisible
						? 'opacity-100 translate-y-0'
						: 'opacity-0 translate-y-4'} overflow-hidden"
				>
					<button
						class="w-full px-6 py-5 text-left flex justify-between items-center group/btn"
						onclick={() => (activeFaq = activeFaq === 4 ? null : 4)}
					>
						<div class="flex items-center gap-4">
							<span
								class="text-[10px] font-bold tracking-[0.2em] text-[#A1A1A1] uppercase"
								>04</span
							>
							<span class="text-base font-bold text-[#141414]"
								>Who is this not for?</span
							>
						</div>
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
							class="text-[#8F8F8F] transition-transform duration-300 {activeFaq ===
							4
								? 'rotate-180'
								: ''}"><path d="m6 9 6 6 6-6" /></svg
						>
					</button>
					{#if activeFaq === 4}
						<div
							transition:slide={{ duration: 300 }}
							class="px-8 pb-8 pt-0"
						>
							<div
								class="h-[1px] w-full bg-[#141414]/5 mb-6"
							></div>
							<p
								class="text-[#4A4A4F] text-lg leading-relaxed max-w-3xl"
							>
								This system is not a fit for companies without a
								proven offer, those unable to handle increased
								volume, or operators who lack the resources to
								manage lead flow. We work with serious agencies
								and staging companies ready to scale
								systematically.
							</p>
						</div>
					{/if}
				</div>

				<!-- FAQ 05 -->
				<div
					class="relative group rounded-[22px] bg-white border border-[#EBEBEB] shadow-[0_1px_3px_rgba(0,0,0,0.02),0_10px_40px_rgba(0,0,0,0.04)] transition-all duration-300 delay-[250ms] {faqVisible
						? 'opacity-100 translate-y-0'
						: 'opacity-0 translate-y-4'} overflow-hidden"
				>
					<button
						class="w-full px-6 py-5 text-left flex justify-between items-center group/btn"
						onclick={() => (activeFaq = activeFaq === 5 ? null : 5)}
					>
						<div class="flex items-center gap-4">
							<span
								class="text-[10px] font-bold tracking-[0.2em] text-[#A1A1A1] uppercase"
								>05</span
							>
							<span class="text-base font-bold text-[#141414]"
								>What is required to start?</span
							>
						</div>
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
							class="text-[#8F8F8F] transition-transform duration-300 {activeFaq ===
							5
								? 'rotate-180'
								: ''}"><path d="m6 9 6 6 6-6" /></svg
						>
					</button>
					{#if activeFaq === 5}
						<div
							transition:slide={{ duration: 300 }}
							class="px-8 pb-8 pt-0"
						>
							<div
								class="h-[1px] w-full bg-[#141414]/5 mb-6"
							></div>
							<p
								class="text-[#4A4A4F] text-lg leading-relaxed max-w-3xl"
							>
								To launch, we need your core offer and
								performance proof, your target market
								parameters, and a dedicated point of contact to
								handle incoming replies and book appointments.
							</p>
						</div>
					{/if}
				</div>

				<!-- FAQ 06 -->
				<div
					class="relative group rounded-[22px] bg-white border border-[#EBEBEB] shadow-[0_1px_3px_rgba(0,0,0,0.02),0_10px_40px_rgba(0,0,0,0.04)] transition-all duration-300 delay-[300ms] {faqVisible
						? 'opacity-100 translate-y-0'
						: 'opacity-0 translate-y-4'} overflow-hidden"
				>
					<button
						class="w-full px-6 py-5 text-left flex justify-between items-center group/btn"
						onclick={() => (activeFaq = activeFaq === 6 ? null : 6)}
					>
						<div class="flex items-center gap-4">
							<span
								class="text-[10px] font-bold tracking-[0.2em] text-[#A1A1A1] uppercase"
								>06</span
							>
							<span class="text-base font-bold text-[#141414]"
								>Will this affect our domain reputation?</span
							>
						</div>
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
							class="text-[#8F8F8F] transition-transform duration-300 {activeFaq ===
							6
								? 'rotate-180'
								: ''}"><path d="m6 9 6 6 6-6" /></svg
						>
					</button>
					{#if activeFaq === 6}
						<div
							transition:slide={{ duration: 300 }}
							class="px-8 pb-8 pt-0"
						>
							<div
								class="h-[1px] w-full bg-[#141414]/5 mb-6"
							></div>
							<p
								class="text-[#4A4A4F] text-lg leading-relaxed max-w-3xl"
							>
								We do not use your main domain for outbound
								activity. We set up isolated sending
								infrastructure with dedicated domains and
								professional authentication to ensure your
								primary reputation remains protected.
							</p>
						</div>
					{/if}
				</div>

				<!-- FAQ 07 -->
				<div
					class="relative group rounded-[22px] bg-white border border-[#EBEBEB] shadow-[0_1px_3px_rgba(0,0,0,0.02),0_10px_40px_rgba(0,0,0,0.04)] transition-all duration-300 delay-[350ms] {faqVisible
						? 'opacity-100 translate-y-0'
						: 'opacity-0 translate-y-4'} overflow-hidden"
				>
					<button
						class="w-full px-6 py-5 text-left flex justify-between items-center group/btn"
						onclick={() => (activeFaq = activeFaq === 7 ? null : 7)}
					>
						<div class="flex items-center gap-4">
							<span
								class="text-[10px] font-bold tracking-[0.2em] text-[#A1A1A1] uppercase"
								>07</span
							>
							<span class="text-base font-bold text-[#141414]"
								>What is the timeline for results?</span
							>
						</div>
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
							class="text-[#8F8F8F] transition-transform duration-300 {activeFaq ===
							7
								? 'rotate-180'
								: ''}"><path d="m6 9 6 6 6-6" /></svg
						>
					</button>
					{#if activeFaq === 7}
						<div
							transition:slide={{ duration: 300 }}
							class="px-8 pb-8 pt-0"
						>
							<div
								class="h-[1px] w-full bg-[#141414]/5 mb-6"
							></div>
							<p
								class="text-[#4A4A4F] text-lg leading-relaxed max-w-3xl"
							>
								The process moves from infrastructure setup to
								inbox warm-up and launch. You will typically see
								initial replies shortly after the system goes
								live, with performance optimized weekly through
								data-driven iterations.
							</p>
						</div>
					{/if}
				</div>

				<!-- FAQ 08 -->
				<div
					class="relative group rounded-[22px] bg-white border border-[#EBEBEB] shadow-[0_1px_3px_rgba(0,0,0,0.02),0_10px_40px_rgba(0,0,0,0.04)] transition-all duration-300 delay-[400ms] {faqVisible
						? 'opacity-100 translate-y-0'
						: 'opacity-0 translate-y-4'} overflow-hidden"
				>
					<button
						class="w-full px-6 py-5 text-left flex justify-between items-center group/btn"
						onclick={() => (activeFaq = activeFaq === 8 ? null : 8)}
					>
						<div class="flex items-center gap-4">
							<span
								class="text-[10px] font-bold tracking-[0.2em] text-[#A1A1A1] uppercase"
								>08</span
							>
							<span class="text-base font-bold text-[#141414]"
								>How does this differ from other agencies?</span
							>
						</div>
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
							class="text-[#8F8F8F] transition-transform duration-300 {activeFaq ===
							8
								? 'rotate-180'
								: ''}"><path d="m6 9 6 6 6-6" /></svg
						>
					</button>
					{#if activeFaq === 8}
						<div
							transition:slide={{ duration: 300 }}
							class="px-8 pb-8 pt-0"
						>
							<div
								class="h-[1px] w-full bg-[#141414]/5 mb-6"
							></div>
							<p
								class="text-[#4A4A4F] text-lg leading-relaxed max-w-3xl"
							>
								Unlike agencies that sell generic outreach, we
								install a high-performance customer acquisition
								engine. This includes signal-based targeting,
								deliverability-first infrastructure, and a
								repeatability-focused reply process.
							</p>
						</div>
					{/if}
				</div>
			</div>
		</div>
	</section>

	<!-- SECTION 4: FINAL CTA -->
	<section class="pt-16 pb-12 md:pb-16 bg-white relative">
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
						><path
							d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"
						/></svg
					>
					<span
						class="text-[10px] font-bold text-white tracking-[0.2em] uppercase"
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

					<div
						class="relative z-10 flex flex-col items-center text-center"
					>
						<h2
							class="text-2xl md:text-[40px] font-bold tracking-tight mb-10 leading-[1.2] md:leading-[1.15] text-gradient-metallic-dark max-w-[800px] transition-[opacity,transform] duration-1000 delay-100 {finalCTAVisible
								? 'opacity-100 translate-y-0'
								: 'opacity-0 translate-y-8'}"
						>
							If you want more leads without hiring or guessing,
							this is it.
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
								<span
									class="relative z-10 flex items-center gap-2 font-semibold"
								>
									Book 15 realtor calls
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
										><path d="M5 12h14" /><path
											d="m12 5 7 7-7 7"
										/></svg
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
									15 qualified realtor calls in your calendar in
									90 days guaranteed, or you get a full refund.
								</p>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>
</div>
