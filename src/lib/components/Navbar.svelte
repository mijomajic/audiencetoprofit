<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { fly, fade } from 'svelte/transition';
	import { cubicOut } from 'svelte/easing';

	let mobileMenuOpen = $state(false);

	function toggleMenu() {
		mobileMenuOpen = !mobileMenuOpen;
	}

	function closeMenu() {
		mobileMenuOpen = false;
	}
</script>

<nav
	class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 border-b border-white/5 {mobileMenuOpen
		? 'bg-[#141414]'
		: 'bg-[#141414]/40 backdrop-blur-xl supports-[backdrop-filter]:bg-[#141414]/20'}"
>
	<div class="container mx-auto px-6 h-20 flex items-center justify-between">
		<!-- Logo -->
		<a href="/" class="flex-shrink-0 group">
			<!-- Desktop Logo -->
			<img
				src="/logo/A2P_Logo_White_Upscaled.svg"
				alt="MMDIGITALS"
				class="hidden md:block h-10 w-auto object-contain brightness-0 invert opacity-90 group-hover:opacity-100 transition-opacity"
			/>
			<!-- Mobile Wordmark -->
			<img
				src="/logo/A2P_WORDMARK_MOBILE_WHITE.svg"
				alt="MMDIGITALS"
				class="block md:hidden h-[18px] w-auto object-contain"
			/>
		</a>

		<!-- Desktop Navigation -->
		<div class="hidden md:flex items-center gap-10">
			<a
				href="/"
				class="text-[15px] font-medium text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors duration-300 tracking-wide"
			>
				Home
			</a>
			<a
				href="https://www.instagram.com/themijomajic/"
				target="_blank"
				rel="noopener noreferrer"
				class="text-[15px] font-medium text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors duration-300 tracking-wide"
			>
				Instagram
			</a>
			<a
				href="https://www.youtube.com/@mijolaunches"
				target="_blank"
				rel="noopener noreferrer"
				class="text-[15px] font-medium text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors duration-300 tracking-wide"
			>
				Youtube
			</a>
			<Button
				href="/apply"
				class="h-10 px-6 text-[13px] font-medium rounded-full bg-white/10 border border-white/25 text-white hover:bg-white/15 hover:shadow-[0_0_20px_rgba(255,255,255,0.1)] transition-all duration-300 backdrop-blur-sm"
			>
				Book a Call
			</Button>
		</div>

		<!-- Mobile Menu Button -->
		<button
			onclick={toggleMenu}
			class="md:hidden relative z-50 p-2 text-white hover:text-white/80 transition-colors w-10 h-10 flex items-center justify-center"
			aria-label="Toggle menu"
		>
			<div class="relative w-6 h-5 flex items-center justify-center">
				<span
					class="absolute h-0.5 bg-current transition-all duration-300 {mobileMenuOpen
						? 'w-6 rotate-45'
						: 'w-6 -translate-y-2'}"
				></span>
				<span
					class="absolute h-0.5 bg-current transition-all duration-300 {mobileMenuOpen
						? 'w-0 opacity-0'
						: 'w-6'}"
				></span>
				<span
					class="absolute h-0.5 bg-current transition-all duration-300 {mobileMenuOpen
						? 'w-6 -rotate-45'
						: 'w-6 translate-y-2'}"
				></span>
			</div>
		</button>
	</div>

	<!-- Mobile Menu Overlay -->
	{#if mobileMenuOpen}
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			class="fixed inset-0 bg-black/60 backdrop-blur-sm z-30 md:hidden"
			onclick={closeMenu}
			transition:fade={{ duration: 300 }}
		></div>
	{/if}

	<!-- Mobile Menu -->
	{#if mobileMenuOpen}
		<div
			transition:fly={{ x: 300, duration: 400, easing: cubicOut }}
			class="md:hidden bg-[#141414] border-l border-white/10 fixed w-full sm:w-80 right-0 top-0 shadow-2xl h-screen z-40"
		>
			<div class="flex flex-col p-8 gap-8 items-start pt-24">
				<a
					href="/"
					onclick={closeMenu}
					class="w-full flex flex-col gap-1 border-b border-white/10 pb-4 group"
				>
					<span class="text-xl font-bold text-white group-hover:text-white/80 transition-colors"
						>Home</span
					>
					<span class="text-sm text-[#8F8F8F] font-light">Return to main page</span>
				</a>
				<a
					href="https://www.instagram.com/themijomajic/"
					target="_blank"
					onclick={closeMenu}
					class="w-full flex flex-col gap-1 border-b border-white/10 pb-4 group"
				>
					<span class="text-xl font-bold text-white group-hover:text-white/80 transition-colors"
						>Instagram</span
					>
					<span class="text-sm text-[#8F8F8F] font-light">Follow for daily content</span>
				</a>
				<a
					href="https://www.youtube.com/@mijolaunches"
					target="_blank"
					onclick={closeMenu}
					class="w-full flex flex-col gap-1 border-b border-white/10 pb-4 group"
				>
					<span class="text-xl font-bold text-white group-hover:text-white/80 transition-colors"
						>Youtube</span
					>
					<span class="text-sm text-[#8F8F8F] font-light">Watch full breakdowns</span>
				</a>
				<Button
					href="/apply"
					onclick={closeMenu}
					class="h-14 px-10 text-[15px] font-medium rounded-full bg-white/10 border border-white/25 text-white hover:bg-white/15 hover:shadow-[0_0_20px_rgba(255,255,255,0.1)] transition-all duration-300 backdrop-blur-sm mt-4"
				>
					Book a Call
				</Button>
			</div>
		</div>
	{/if}
</nav>
