<script lang="ts">
	import { Button } from '$lib/components/ui/button';
</script>

<nav
	class="fixed top-0 left-0 right-0 z-50 transition-[background-color,backdrop-filter] duration-300 border-b border-white/5 bg-[#141414]/95 backdrop-blur-xl supports-[backdrop-filter]:bg-[#141414]/90"
>
	<div class="container mx-auto px-6 h-20 flex items-center justify-between">
		<!-- Logo -->
		<a href="/" class="flex-shrink-0 group">
			<!-- Desktop Logo -->
			<img
				src="/logo/EASTLINE CONSULTING.svg?v=2"
				alt="EASTLINE CONSULTING"
				class="hidden md:block h-10 w-auto object-contain brightness-0 invert opacity-90 group-hover:opacity-100 transition-opacity"
			/>
			<!-- Mobile Wordmark -->
			<img
				src="/logo/EASTLINE CONSULTING.svg?v=2"
				alt="EASTLINE CONSULTING"
				class="block md:hidden h-[28px] w-auto object-contain text-white"
			/>
		</a>

		<!-- Navigation CTA -->
		<div class="flex items-center gap-6">
			<a
				href="https://www.linkedin.com/in/mijomajic/"
				target="_blank"
				class="text-[12px] md:text-[13px] font-medium text-white/60 hover:text-white transition-colors"
			>
				LinkedIn
			</a>
			<Button
				href="https://calendly.com/eastlineconsulting/30min"
				target="_blank"
				class="h-9 md:h-10 px-4 md:px-6 text-[12px] md:text-[13px] font-medium rounded-full bg-white/10 border border-white/25 text-white hover:bg-white/15 hover:shadow-[0_0_20px_rgba(255,255,255,0.1)] transition-[background-color,box-shadow] duration-300 backdrop-blur-sm"
			>
				Book 15 qualified calls
			</Button>
		</div>
	</div>
</nav>
