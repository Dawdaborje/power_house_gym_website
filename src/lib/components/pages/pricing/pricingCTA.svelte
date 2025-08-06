<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});
</script>

<section class="relative overflow-hidden bg-black pt-24 pb-12">
	<!-- Background Pattern -->
	<div class="absolute inset-0 opacity-5">
		<svg class="h-full w-full" xmlns="http://www.w3.org/2000/svg">
			<defs>
				<pattern id="pricing-cta-grid" width="80" height="80" patternUnits="userSpaceOnUse">
					<circle cx="40" cy="40" r="2" fill="white" opacity="0.4" />
					<circle cx="0" cy="0" r="1" fill="white" opacity="0.2" />
					<circle cx="80" cy="80" r="1" fill="white" opacity="0.2" />
				</pattern>
			</defs>
			<rect width="100%" height="100%" fill="url(#pricing-cta-grid)" />
		</svg>
	</div>

	<!-- Gradient Overlay -->
	<div class="absolute inset-0 bg-gradient-to-br from-black via-transparent to-black/80"></div>

	<div class="relative z-10 mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="text-center">
			<!-- Badge -->
			<div
				class="mb-8 inline-flex transform items-center rounded-full border border-white/20 bg-white/10 px-6 py-3 backdrop-blur-md transition-all delay-200 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<span class="text-lg font-bold text-white">⚡ START YOUR TRANSFORMATION TODAY</span>
			</div>

			<!-- Main Heading -->
			<h2
				class="mb-8 transform text-5xl font-black text-white transition-all delay-400 duration-1000 md:text-6xl lg:text-7xl {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				READY TO
				<span
					class="block bg-gradient-to-r from-white via-gray-200 to-gray-400 bg-clip-text text-transparent"
				>
					POWER UP?
				</span>
			</h2>

			<!-- Subtitle -->
			<p
				class="mx-auto mb-12 max-w-4xl transform text-xl leading-relaxed text-gray-300 transition-all delay-600 duration-1000 md:text-2xl {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				Join thousands of members who've transformed their lives at Power House Elite Fitness. Your
				journey to peak performance starts with a single step.
			</p>

			<!-- Special Offer -->
			<div
				class="mx-auto mb-12 max-w-2xl transform rounded-3xl border border-green-500/30 bg-green-500/10 p-6 backdrop-blur-md transition-all delay-800 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<h3 class="mb-3 text-2xl font-bold text-white">Limited Time Offer</h3>
				<div class="mb-2 text-4xl font-black text-green-400">50% OFF</div>
				<p class="mb-4 text-gray-300">Your first month when you sign up for any membership plan</p>
				<div class="flex items-center justify-center space-x-4 text-sm text-gray-400">
					<span>⏰ Offer ends in 48 hours</span>
					<span>•</span>
					<span>🎯 New members only</span>
				</div>
			</div>

			<!-- Primary CTA Buttons -->
			<div
				class="mb-16 flex transform flex-col gap-6 transition-all delay-1000 duration-1000 sm:flex-row sm:justify-center {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<button
					class="group relative overflow-hidden rounded-2xl bg-white px-12 py-6 text-xl font-bold text-black transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-white/25"
				>
					<span class="relative z-10">CLAIM 7-DAY FREE TRIAL</span>
					<div
						class="absolute inset-0 translate-x-full transform bg-black transition-transform duration-300 group-hover:translate-x-0"
					></div>
					<span
						class="absolute inset-0 z-10 flex items-center justify-center text-xl font-bold text-white opacity-0 transition-opacity duration-300 group-hover:opacity-100"
					>
						CLAIM 7-DAY FREE TRIAL
					</span>
				</button>

				<button
					class="flex items-center justify-center gap-4 rounded-2xl border-2 border-white bg-transparent px-12 py-6 text-xl font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
				>
					<span>BROWSE MEMBERSHIP PLANS</span>
					<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M13 7l5 5m0 0l-5 5m5-5H6"
						/>
					</svg>
				</button>
			</div>

			<!-- Secondary Options -->
			<div
				class="mb-16 transform transition-all delay-1200 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<p class="mb-6 text-gray-400">Prefer to speak with someone first?</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Schedule a Tour
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Talk to an Expert
					</button>
				</div>
			</div>

			<!-- Trust Indicators -->
			<div
				class="mx-auto grid max-w-4xl transform grid-cols-2 gap-8 transition-all delay-1400 duration-1000 md:grid-cols-4 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="text-center">
					<div class="mb-2 text-3xl font-black text-white">2000+</div>
					<div class="text-sm text-gray-400">Happy Members</div>
				</div>
				<div class="text-center">
					<div class="mb-2 text-3xl font-black text-white">4.9/5</div>
					<div class="text-sm text-gray-400">Average Rating</div>
				</div>
				<div class="text-center">
					<div class="mb-2 text-3xl font-black text-white">98%</div>
					<div class="text-sm text-gray-400">Member Retention</div>
				</div>
				<div class="text-center">
					<div class="mb-2 text-3xl font-black text-white">24/7</div>
					<div class="text-sm text-gray-400">Support Available</div>
				</div>
			</div>

			<!-- Money Back Guarantee -->
			<div
				class="mt-16 transform transition-all delay-1600 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div
					class="mx-auto max-w-2xl rounded-2xl border border-green-500/20 bg-green-500/10 p-6 backdrop-blur-md"
				>
					<div class="mb-3 text-3xl">✅</div>
					<h4 class="mb-3 text-xl font-bold text-white">30-Day Money-Back Guarantee</h4>
					<p class="text-gray-300">
						Not completely satisfied? Get a full refund within 30 days, no questions asked. We're
						that confident you'll love your Power House experience.
					</p>
				</div>
			</div>

			<!-- Contact Information -->
			<div
				class="mt-12 transform transition-all delay-1800 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="grid grid-cols-1 gap-6 md:grid-cols-3">
					<div class="text-center">
						<div class="mb-3 text-2xl">📞</div>
						<h5 class="mb-2 font-semibold text-white">Call Us</h5>
						<p class="text-gray-300">(555) 123-4567</p>
						<p class="text-sm text-gray-500">Mon-Sun 6am-10pm</p>
					</div>
					<div class="text-center">
						<div class="mb-3 text-2xl">📍</div>
						<h5 class="mb-2 font-semibold text-white">Visit Us</h5>
						<p class="text-gray-300">123 Fitness Street<br />City, State 12345</p>
						<p class="text-sm text-gray-500">Open 24/7 for members</p>
					</div>
					<div class="text-center">
						<div class="mb-3 text-2xl">💬</div>
						<h5 class="mb-2 font-semibold text-white">Chat With Us</h5>
						<p class="text-gray-300">Live chat available</p>
						<p class="text-sm text-gray-500">Response within 2 minutes</p>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Background Decorative Elements -->
	<div class="absolute top-20 right-12 h-40 w-40 rounded-full bg-white/5 blur-xl"></div>
	<div class="absolute bottom-20 left-12 h-32 w-32 rounded-full bg-white/10 blur-xl"></div>
	<div class="absolute right-4 bottom-40 h-48 w-48 rounded-full bg-white/5 blur-xl"></div>
</section>
