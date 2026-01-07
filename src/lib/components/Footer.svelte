<script lang="ts">
	const year = new Date().getFullYear();
</script>

<footer class="py-6 bg-[#141414] border-t border-white/10">
	<div class="container mx-auto px-4">
		<div class="flex flex-col md:flex-row items-center justify-between gap-4 md:gap-0">
			<!-- Logo & Copyright -->
			<div class="flex items-center gap-4">
				<img
					src="/logo/A2P_Logo_White_Upscaled.svg"
					alt="AudienceToProfit"
					class="h-5 w-auto opacity-80"
				/>
				<p class="text-xs text-[#8F8F8F]">
					&copy; {year} AudienceToProfit. All rights reserved.
				</p>
			</div>

			<!-- Links -->
			<div class="flex items-center gap-6">
				<a href="/" class="text-xs text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors">Home</a>
				<a
					href="https://www.instagram.com/themijomajic/"
					target="_blank"
					rel="noopener noreferrer"
					class="text-xs text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors">Instagram</a
				>
				<a
					href="https://www.youtube.com/@mijolaunches"
					target="_blank"
					rel="noopener noreferrer"
					class="text-xs text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors">Youtube</a
				>
				<a href="/apply" class="text-xs text-[#8F8F8F] hover:text-[#F0F0F0] transition-colors"
					>Book a Call</a
				>
			</div>
		</div>
	</div>
</footer>
