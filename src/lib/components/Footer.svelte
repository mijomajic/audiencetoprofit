<script lang="ts">
	const year = new Date().getFullYear();
</script>

<footer class="py-6 bg-[#141414] border-t border-white/10">
	<div class="max-w-6xl mx-auto px-6">
		<div class="flex flex-col md:flex-row items-center justify-between gap-4 md:gap-0">
			<!-- Logo & Copyright -->
			<div class="flex items-center gap-4">
				<img
					src="/logo/EASTLINE CONSULTING.svg?v=2"
					alt="Eastline Consulting"
					class="h-6 w-auto brightness-0 invert opacity-60"
				/>
				<p class="text-xs text-[#8F8F8F]">
					&copy; {year} Eastline Consulting. All rights reserved.
				</p>
			</div>

			<!-- Links -->
			<div class="flex items-center gap-6">
				<a
					href="https://www.linkedin.com/in/mijomajic/"
					target="_blank"
					class="text-xs text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors">LinkedIn</a
				>
				<a
					href="https://calendly.com/eastlineconsulting/30min"
					target="_blank"
					class="text-xs text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors"
					>Book 15 qualified calls</a
				>
			</div>
		</div>
	</div>
</footer>
