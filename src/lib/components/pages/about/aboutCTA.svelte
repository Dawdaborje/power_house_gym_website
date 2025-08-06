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
				<pattern id="about-cta-grid" width="80" height="80" patternUnits="userSpaceOnUse">
					<circle cx="40" cy="40" r="2" fill="white" opacity="0.4" />
					<circle cx="0" cy="0" r="1" fill="white" opacity="0.2" />
					<circle cx="80" cy="80" r="1" fill="white" opacity="0.2" />
				</pattern>
			</defs>
			<rect width="100%" height="100%" fill="url(#about-cta-grid)" />
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
				<span class="text-lg font-bold text-white">🚀 JOIN THE POWER HOUSE FAMILY</span>
			</div>

			<!-- Main Heading -->
			<h2
				class="mb-8 transform text-5xl font-black text-white transition-all delay-400 duration-1000 md:text-6xl lg:text-7xl {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				READY TO BE PART OF
				<span
					class="block bg-gradient-to-r from-white via-gray-200 to-gray-400 bg-clip-text text-transparent"
				>
					OUR STORY?
				</span>
			</h2>

			<!-- Subtitle -->
			<p
				class="mx-auto mb-12 max-w-4xl transform text-xl leading-relaxed text-gray-300 transition-all delay-600 duration-1000 md:text-2xl {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				Now that you know who we are and what we stand for, we invite you to experience the Power
				House difference for yourself. Your transformation story starts here.
			</p>

			<!-- Why Choose Us Summary -->
			<div
				class="mx-auto mb-16 grid max-w-5xl transform grid-cols-1 gap-8 transition-all delay-800 duration-1000 md:grid-cols-3 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-4 text-4xl">🏆</div>
					<h3 class="mb-3 text-lg font-bold text-white">Proven Excellence</h3>
					<p class="text-gray-300">
						Award-winning facility with 6 years of transforming lives and exceeding expectations.
					</p>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-4 text-4xl">👥</div>
					<h3 class="mb-3 text-lg font-bold text-white">Expert Team</h3>
					<p class="text-gray-300">
						50+ certified professionals with 300+ years of combined experience and 200+
						certifications.
					</p>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-4 text-4xl">🌟</div>
					<h3 class="mb-3 text-lg font-bold text-white">Community Impact</h3>
					<p class="text-gray-300">
						More than a gym - we're a community that gives back and makes a difference beyond our
						walls.
					</p>
				</div>
			</div>

			<!-- CTA Buttons -->
			<div
				class="mb-16 flex transform flex-col gap-6 transition-all delay-1000 duration-1000 sm:flex-row sm:justify-center {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<button
					class="group relative overflow-hidden rounded-2xl bg-white px-12 py-6 text-xl font-bold text-black transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-white/25"
				>
					<span class="relative z-10">START YOUR JOURNEY TODAY</span>
					<div
						class="absolute inset-0 translate-x-full transform bg-black transition-transform duration-300 group-hover:translate-x-0"
					></div>
					<span
						class="absolute inset-0 z-10 flex items-center justify-center text-xl font-bold text-white opacity-0 transition-opacity duration-300 group-hover:opacity-100"
					>
						START YOUR JOURNEY TODAY
					</span>
				</button>

				<button
					class="flex items-center justify-center gap-4 rounded-2xl border-2 border-white bg-transparent px-12 py-6 text-xl font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
				>
					<span>SCHEDULE A TOUR</span>
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

			<!-- Next Steps -->
			<div
				class="mb-16 transform transition-all delay-1200 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<h3 class="mb-8 text-2xl font-bold text-white">Take the Next Step</h3>
				<div class="grid grid-cols-1 gap-6 md:grid-cols-3">
					<div class="rounded-xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
						<div class="mb-3 text-2xl">📞</div>
						<h4 class="mb-2 text-lg font-bold text-white">Call Us</h4>
						<p class="mb-3 text-gray-300">Speak with our team about membership options</p>
						<p class="text-sm font-medium text-white">(555) 123-4567</p>
					</div>

					<div class="rounded-xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
						<div class="mb-3 text-2xl">📍</div>
						<h4 class="mb-2 text-lg font-bold text-white">Visit Us</h4>
						<p class="mb-3 text-gray-300">See our facilities and meet our team in person</p>
						<p class="text-sm font-medium text-white">123 Fitness Street, City</p>
					</div>

					<div class="rounded-xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
						<div class="mb-3 text-2xl">💻</div>
						<h4 class="mb-2 text-lg font-bold text-white">Browse Online</h4>
						<p class="mb-3 text-gray-300">Explore our programs and pricing plans</p>
						<p class="text-sm font-medium text-white">Available 24/7</p>
					</div>
				</div>
			</div>

			<!-- Trust Indicators -->
			<div
				class="mx-auto grid max-w-4xl transform grid-cols-2 gap-8 transition-all delay-1400 duration-1000 md:grid-cols-4 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="text-center">
					<div class="mb-2 text-3xl font-black text-white">15K+</div>
					<div class="text-sm text-gray-400">Lives Transformed</div>
				</div>
				<div class="text-center">
					<div class="mb-2 text-3xl font-black text-white">98%</div>
					<div class="text-sm text-gray-400">Member Satisfaction</div>
				</div>
				<div class="text-center">
					<div class="mb-2 text-3xl font-black text-white">6</div>
					<div class="text-sm text-gray-400">Years of Excellence</div>
				</div>
				<div class="text-center">
					<div class="mb-2 text-3xl font-black text-white">24/7</div>
					<div class="text-sm text-gray-400">Support & Access</div>
				</div>
			</div>

			<!-- Final Message -->
			<div
				class="mt-16 transform transition-all delay-1600 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div
					class="mx-auto max-w-3xl rounded-2xl border border-white/20 bg-gradient-to-r from-white/10 to-white/5 p-8 backdrop-blur-md"
				>
					<h4 class="mb-4 text-xl font-bold text-white">Your Success is Our Mission</h4>
					<p class="leading-relaxed text-gray-300">
						At Power House Elite Fitness, we don't just provide a place to work out - we provide a
						community, expertise, and unwavering support for your fitness journey. Join the
						thousands who have already discovered what it means to be part of something
						extraordinary.
					</p>
				</div>
			</div>

			<!-- Social Proof -->
			<div
				class="mt-12 transform transition-all delay-1800 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="flex items-center justify-center space-x-8 text-gray-400">
					<span class="text-sm">⭐ 4.9/5 Rating</span>
					<span class="text-sm">•</span>
					<span class="text-sm">🏆 Award Winning</span>
					<span class="text-sm">•</span>
					<span class="text-sm">🎯 Results Driven</span>
				</div>
			</div>
		</div>
	</div>

	<!-- Background Decorative Elements -->
	<div class="absolute top-20 right-12 h-40 w-40 rounded-full bg-white/5 blur-xl"></div>
	<div class="absolute bottom-20 left-12 h-32 w-32 rounded-full bg-white/10 blur-xl"></div>
	<div class="absolute right-4 bottom-40 h-48 w-48 rounded-full bg-white/5 blur-xl"></div>
</section>
