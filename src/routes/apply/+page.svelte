<script lang="ts">
	import { fade, slide, fly } from 'svelte/transition';
	import { enhance } from '$app/forms';

	let step = 0;
	let isSubmitting = false;
	let isSuccess = false;

	// Form Data State
	let formData = {
		companyName: '',
		role: '',
		website: '',
		revenue: '',
		growthSituation: [] as string[],
		bottleneck: '',
		timing: '',
		timingReason: '',
		investmentAligned: '',
		successVision: '',
		email: '',
		phone: ''
	};

	function nextStep() {
		// Basic validation before moving
		if (step === 1 && (!formData.companyName || !formData.role || !formData.website)) return;
		if (step === 2 && !formData.revenue) return;
		if (step === 3 && formData.growthSituation.length === 0) return;
		if (step === 4 && !formData.bottleneck) return;
		if (step === 5) {
			if (!formData.timing) return;
			if (formData.timing === 'Just exploring' && !formData.timingReason) return;
		}
		if (step === 6 && !formData.successVision) return;

		step++;
	}

	function prevStep() {
		if (step > 0) step--;
	}

	async function handleSubmit(e: SubmitEvent) {
		// e.preventDefault() handled by on:submit logic below if we were doing custom fetch,
		// but for Formspree we want the form to actually post OR use fetch API.
		// User requirement: "No backend... Formspree endpoint".
		// We'll use fetch to post to Formspree so we can show the thank you state in-app.

		e.preventDefault();
		isSubmitting = true;

		try {
			const form = e.target as HTMLFormElement;
			const data = new FormData(form);

			const response = await fetch('https://formspree.io/f/xjggvpqz', {
				method: 'POST',
				body: data,
				headers: {
					Accept: 'application/json'
				}
			});

			if (response.ok) {
				isSuccess = true;
			} else {
				alert('Something went wrong. Please try again.');
			}
		} catch (error) {
			alert('Error submitting form. Please check your connection.');
		} finally {
			isSubmitting = false;
		}
	}

	// Options
	const revenues = [
		'Pre-revenue',
		'$1K–$10K',
		'$10K–$20K',
		'$20K–$50K',
		'$50K–$100K',
		'$100K–$200K',
		'$200K+'
	];

	const growthSituations = [
		'We rely mostly on outbound',
		'We rely mostly on inbound/SEO',
		'Paid ads are active but inconsistent',
		'We have traffic but poor conversion',
		'We have users but retention is weak',
		'Growth feels scattered or fragile'
	];

	const bottlenecks = [
		'Not enough qualified demand',
		'Low trial → paid conversion',
		'Long time-to-value',
		'Poor onboarding / activation',
		'Weak retention or expansion',
		'No clear system or ownership'
	];

	const timings = ['Immediately', 'Within 30 days', '30–60 days', 'Just exploring'];
</script>

<svelte:head>
	<title>Apply to Install a Growth System - Eastline</title>
</svelte:head>

<div
	class="min-h-screen bg-white text-[#141414] font-sans selection:bg-[#141414] selection:text-white flex items-center justify-center p-4"
>
	{#if isSuccess}
		<div class="max-w-xl w-full text-center" in:fly={{ y: 20, duration: 600, delay: 200 }}>
			<div
				class="w-16 h-16 bg-[#F5F5F5] rounded-full flex items-center justify-center mx-auto mb-8"
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					stroke="#141414"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"><path d="M20 6 9 17l-5-5" /></svg
				>
			</div>
			<h1 class="text-3xl md:text-4xl font-bold tracking-tight mb-6">Application received.</h1>
			<p class="text-[#4A4A4F] text-lg leading-relaxed mb-8">
				Thanks for applying. We’ll review your answers and determine whether the Growth Print
				Playbook is a fit.
			</p>
			<p class="text-[#4A4A4F] text-lg leading-relaxed mb-12">
				If it is, you’ll receive a follow-up with next steps. <br class="hidden md:block" />
				If not, we’ll still point you in the right direction.
			</p>
			<a
				href="/"
				class="inline-flex items-center justify-center h-12 px-8 rounded-full bg-[#FAFAFA] border border-[#EBEBEB] text-[#141414] font-medium hover:bg-[#F0F0F0] transition-colors cursor-pointer"
			>
				Back to Website
			</a>
		</div>
	{:else}
		<form on:submit={handleSubmit} class="max-w-xl w-full relative">
			<!-- Navigation & Stepper -->
			<div class="mb-12">
				<div class="flex items-center justify-between mb-8">
					<button
						type="button"
						on:click={() => (step === 0 ? (window.location.href = '/') : prevStep())}
						class="flex items-center gap-2 text-[#8F8F8F] hover:text-[#141414] transition-all group cursor-pointer"
					>
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
							class="transition-transform group-hover:-translate-x-1"
							><path d="m15 18-6-6 6-6" /></svg
						>
						<span class="text-sm font-medium">{step === 0 ? 'Back to site' : 'Go back'}</span>
					</button>

					{#if step > 0}
						<div class="text-[10px] font-bold tracking-[0.2em] uppercase text-[#8F8F8F]">
							Step {step} <span class="text-[#EBEBEB] mx-1">/</span> 7
						</div>
					{/if}
				</div>

				{#if step > 0}
					<div class="flex gap-1.5 h-1">
						{#each Array(7) as _, i}
							<div
								class="flex-1 rounded-full transition-all duration-500 {i < step
									? 'bg-[#141414]'
									: 'bg-[#F5F5F5]'}"
							></div>
						{/each}
					</div>
				{/if}
			</div>

			<!-- Step 0: Intro -->
			{#if step === 0}
				<div class="text-center md:text-left" in:fly={{ y: 20, duration: 600 }}>
					<div
						class="inline-block px-3 py-1 rounded-full bg-[#FAFAFA] border border-[#EBEBEB] mb-6"
					>
						<span class="text-[10px] uppercase tracking-[0.15em] font-bold text-[#141414]"
							>Application</span
						>
					</div>

					<h1 class="text-3xl md:text-5xl font-bold tracking-tight leading-[1.1] mb-6">
						Apply to Install a Complete SaaS Growth System
					</h1>
					<p class="text-[#4A4A4F] text-lg leading-relaxed mb-10 max-w-lg">
						This is not a generic agency service. We work with a small number of B2B SaaS companies
						that already have product-market fit and want a repeatable growth engine.
					</p>

					<div class="space-y-4 mb-12">
						<div class="flex items-center gap-3 text-[#141414]">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								fill="none"
								stroke="currentColor"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"><path d="M20 6 9 17l-5-5" /></svg
							>
							<span>Built in 8 weeks</span>
						</div>
						<div class="flex items-center gap-3 text-[#141414]">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								fill="none"
								stroke="currentColor"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"><path d="M20 6 9 17l-5-5" /></svg
							>
							<span>Replaces an entire growth department</span>
						</div>
						<div class="flex items-center gap-3 text-[#141414]">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								fill="none"
								stroke="currentColor"
								stroke-width="2"
								stroke-linecap="round"
								stroke-linejoin="round"><path d="M20 6 9 17l-5-5" /></svg
							>
							<span>Designed for SaaS doing $20K–$200K/month</span>
						</div>
					</div>

					<button
						type="button"
						on:click={nextStep}
						class="w-full md:w-auto h-14 px-10 rounded-full bg-[#141414] text-white font-semibold flex items-center justify-center gap-2 hover:bg-[#262626] hover:scale-[1.02] active:scale-[0.98] transition-all shadow-lg shadow-black/5 cursor-pointer"
					>
						Start Application <span class="text-lg">→</span>
					</button>
				</div>
			{/if}

			<!-- Step 1: Basic Qual -->
			{#if step === 1}
				<div in:fly={{ y: 20, duration: 300, delay: 100 }}>
					<h2 class="text-2xl font-bold mb-8">Tell us about your company.</h2>
					<div class="space-y-6">
						<div>
							<label class="block text-sm font-medium text-[#4A4A4F] mb-2" for="company"
								>Company Name</label
							>
							<input
								type="text"
								id="company"
								name="company_name"
								bind:value={formData.companyName}
								class="w-full h-12 px-4 rounded-xl bg-[#FAFAFA] border border-[#EBEBEB] focus:outline-none focus:border-[#141414] focus:ring-1 focus:ring-[#141414] transition-all"
								placeholder="Acme Inc."
								required
							/>
						</div>
						<div>
							<label class="block text-sm font-medium text-[#4A4A4F] mb-2" for="role"
								>Your Role</label
							>
							<select
								id="role"
								name="role"
								bind:value={formData.role}
								class="w-full h-12 px-4 rounded-xl bg-[#FAFAFA] border border-[#EBEBEB] focus:outline-none focus:border-[#141414] focus:ring-1 focus:ring-[#141414] transition-all appearance-none cursor-pointer"
								required
							>
								<option value="" disabled selected>Select your role...</option>
								<option value="Founder / Co-founder">Founder / Co-founder</option>
								<option value="Head of Growth">Head of Growth</option>
								<option value="Other">Other</option>
							</select>
						</div>
						<div>
							<label class="block text-sm font-medium text-[#4A4A4F] mb-2" for="website"
								>Company Website</label
							>
							<input
								type="url"
								id="website"
								name="website"
								bind:value={formData.website}
								class="w-full h-12 px-4 rounded-xl bg-[#FAFAFA] border border-[#EBEBEB] focus:outline-none focus:border-[#141414] focus:ring-1 focus:ring-[#141414] transition-all"
								placeholder="https://acme.com"
								required
							/>
						</div>
					</div>
				</div>
			{/if}

			<!-- Step 2: Revenue -->
			{#if step === 2}
				<div in:fly={{ y: 20, duration: 300, delay: 100 }}>
					<h2 class="text-2xl font-bold mb-2">What’s your current monthly revenue?</h2>
					<p class="text-[#8F8F8F] mb-8">
						We work best with companies that already have product-market fit.
					</p>

					<div class="space-y-3">
						{#each revenues as rev}
							<label
								class="flex items-center p-4 rounded-xl border cursor-pointer transition-all duration-200 {formData.revenue ===
								rev
									? 'bg-[#141414] border-[#141414] text-white'
									: 'bg-white border-[#EBEBEB] text-[#141414] hover:border-[#141414]'}"
							>
								<input
									type="radio"
									name="revenue"
									value={rev}
									bind:group={formData.revenue}
									class="sr-only"
								/>
								<span class="font-medium">{rev}</span>
							</label>
						{/each}
					</div>
				</div>
			{/if}

			<!-- Step 3: Growth Setup -->
			{#if step === 3}
				<div in:fly={{ y: 20, duration: 300, delay: 100 }}>
					<h2 class="text-2xl font-bold mb-8">
						Which best describes your current growth situation?
					</h2>

					<div class="space-y-3">
						{#each growthSituations as situation}
							<label
								class="flex items-center p-4 rounded-xl border cursor-pointer transition-all duration-200 {formData.growthSituation.includes(
									situation
								)
									? 'bg-[#141414] border-[#141414] text-white'
									: 'bg-white border-[#EBEBEB] text-[#141414] hover:border-[#141414]'}"
							>
								<input
									type="checkbox"
									name="growth_situations"
									value={situation}
									bind:group={formData.growthSituation}
									class="sr-only"
								/>
								<span class="font-medium">{situation}</span>
							</label>
						{/each}
					</div>
				</div>
			{/if}

			<!-- Step 4: Bottleneck -->
			{#if step === 4}
				<div in:fly={{ y: 20, duration: 300, delay: 100 }}>
					<h2 class="text-2xl font-bold mb-8">
						What is the single biggest bottleneck holding growth back right now?
					</h2>

					<div class="space-y-3">
						{#each bottlenecks as b}
							<label
								class="flex items-center p-4 rounded-xl border cursor-pointer transition-all duration-200 {formData.bottleneck ===
								b
									? 'bg-[#141414] border-[#141414] text-white'
									: 'bg-white border-[#EBEBEB] text-[#141414] hover:border-[#141414]'}"
							>
								<input
									type="radio"
									name="bottleneck"
									value={b}
									bind:group={formData.bottleneck}
									class="sr-only"
								/>
								<span class="font-medium">{b}</span>
							</label>
						{/each}
					</div>
				</div>
			{/if}

			<!-- Step 5: Intent & Timing -->
			{#if step === 5}
				<div in:fly={{ y: 20, duration: 300, delay: 100 }}>
					<h2 class="text-2xl font-bold mb-8">
						If we were to build this system for you, when would you want it live?
					</h2>

					<div class="space-y-3 mb-6">
						{#each timings as t}
							<label
								class="flex items-center p-4 rounded-xl border cursor-pointer transition-all duration-200 {formData.timing ===
								t
									? 'bg-[#141414] border-[#141414] text-white'
									: 'bg-white border-[#EBEBEB] text-[#141414] hover:border-[#141414]'}"
							>
								<input
									type="radio"
									name="timing"
									value={t}
									bind:group={formData.timing}
									class="sr-only"
								/>
								<span class="font-medium">{t}</span>
							</label>
						{/each}
					</div>

					{#if formData.timing === 'Just exploring'}
						<div class="mt-6" transition:slide>
							<label class="block text-sm font-medium text-[#4A4A4F] mb-2" for="timing_reason"
								>What prompted you to look into this now?</label
							>
							<input
								type="text"
								id="timing_reason"
								name="timing_reason"
								bind:value={formData.timingReason}
								class="w-full h-12 px-4 rounded-xl bg-[#FAFAFA] border border-[#EBEBEB] focus:outline-none focus:border-[#141414] focus:ring-1 focus:ring-[#141414] transition-all"
								required={formData.timing === 'Just exploring'}
							/>
						</div>
					{/if}
				</div>
			{/if}

			<!-- Step 6: Final Open Ended -->
			{#if step === 6}
				<div in:fly={{ y: 20, duration: 300, delay: 100 }}>
					<h2 class="text-2xl font-bold mb-8">
						Briefly describe what success would look like 6 months from now if this system worked
						perfectly.
					</h2>

					<textarea
						name="success_vision"
						bind:value={formData.successVision}
						class="w-full h-40 p-4 rounded-xl bg-[#FAFAFA] border border-[#EBEBEB] focus:outline-none focus:border-[#141414] focus:ring-1 focus:ring-[#141414] transition-all resize-none"
						placeholder="E.g. We have predictable lead flow and..."
						required
					></textarea>
				</div>
			{/if}

			<!-- Step 7: Contact -->
			{#if step === 7}
				<div in:fly={{ y: 20, duration: 300, delay: 100 }}>
					<h2 class="text-2xl font-bold mb-8">Where should we send the next steps?</h2>

					<div class="space-y-6 mb-10">
						<div>
							<label class="block text-sm font-medium text-[#4A4A4F] mb-2" for="email"
								>Best Email</label
							>
							<input
								type="email"
								id="email"
								name="email"
								bind:value={formData.email}
								class="w-full h-12 px-4 rounded-xl bg-[#FAFAFA] border border-[#EBEBEB] focus:outline-none focus:border-[#141414] focus:ring-1 focus:ring-[#141414] transition-all"
								placeholder="you@company.com"
								required
							/>
						</div>
						<div>
							<label class="block text-sm font-medium text-[#4A4A4F] mb-2" for="phone"
								>Phone Number (Optional)</label
							>
							<input
								type="tel"
								id="phone"
								name="phone"
								bind:value={formData.phone}
								class="w-full h-12 px-4 rounded-xl bg-[#FAFAFA] border border-[#EBEBEB] focus:outline-none focus:border-[#141414] focus:ring-1 focus:ring-[#141414] transition-all"
								placeholder="+1 (555) 000-0000"
							/>
						</div>
					</div>

					<button
						type="submit"
						disabled={isSubmitting}
						class="w-full h-14 rounded-full bg-[#141414] text-white font-semibold flex items-center justify-center gap-2 hover:bg-[#262626] transition-all disabled:opacity-70 disabled:cursor-not-allowed cursor-pointer"
					>
						{#if isSubmitting}
							<span>Submitting...</span>
						{:else}
							Submit Application <span class="text-lg">→</span>
						{/if}
					</button>
					<p class="text-center text-xs text-[#8F8F8F] mt-4">
						We review every application personally. If it’s a fit, you’ll hear from us within 48
						hours.
					</p>
				</div>
			{/if}

			<!-- Navigation Buttons for Steps 1-6 -->
			{#if step > 0 && step < 7}
				<div class="flex items-center gap-4 mt-12 pt-8 border-t border-[#F5F5F5]">
					<button
						type="button"
						on:click={prevStep}
						class="h-12 px-8 rounded-full bg-white border border-[#EBEBEB] text-[#141414] font-medium hover:bg-[#FAFAFA] hover:border-[#D1D1D1] active:scale-[0.98] transition-all cursor-pointer"
					>
						Back
					</button>
					<button
						type="button"
						on:click={nextStep}
						class="flex-1 h-12 rounded-full bg-[#141414] text-white font-semibold hover:bg-[#262626] hover:scale-[1.01] active:scale-[0.99] transition-all shadow-md shadow-black/5 cursor-pointer"
					>
						Continue
					</button>
				</div>
			{/if}
		</form>
	{/if}
</div>
