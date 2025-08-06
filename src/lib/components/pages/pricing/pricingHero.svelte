<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let scrollY = 0;

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);

		const handleScroll = () => {
			scrollY = window.scrollY;
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<section class="relative min-h-[85vh] overflow-hidden bg-black">
	<!-- Background Image with Parallax -->
	<div class="absolute inset-0">
		<div
			class="absolute inset-0 bg-cover bg-center bg-no-repeat transition-transform duration-75"
			style="background-image: url('https://images.unsplash.com/photo-1534438327276-14e5300c3a48?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80'); 
			transform: translateY({scrollY * 0.3}px) scale(1.1);"
		></div>

		<!-- Overlay -->
		<div class="absolute inset-0 bg-black/75"></div>
		<div class="absolute inset-0 bg-gradient-to-br from-black/60 via-transparent to-black/80"></div>
	</div>

	<!-- Geometric Pattern Overlay -->
	<div class="absolute inset-0 opacity-10">
		<svg class="h-full w-full" xmlns="http://www.w3.org/2000/svg">
			<defs>
				<pattern id="pricing-grid" width="80" height="80" patternUnits="userSpaceOnUse">
					<circle cx="40" cy="40" r="2" fill="white" opacity="0.4" />
					<circle cx="0" cy="0" r="1" fill="white" opacity="0.2" />
					<circle cx="80" cy="80" r="1" fill="white" opacity="0.2" />
				</pattern>
			</defs>
			<rect width="100%" height="100%" fill="url(#pricing-grid)" />
		</svg>
	</div>

	<!-- Hero Content -->
	<div class="relative z-10 flex min-h-[85vh] items-center">
		<div class="mx-auto w-full max-w-7xl px-4 sm:px-6 lg:px-8">
			<div class="text-center">
				<div
					class="transform transition-all delay-300 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-12 opacity-0'}"
				>
					<!-- Breadcrumb -->
					<div class="mb-8 flex items-center justify-center space-x-2 text-gray-400">
						<a href="/" class="transition-colors hover:text-white">Home</a>
						<svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M9 5l7 7-7 7"
							/>
						</svg>
						<span class="text-white">Pricing</span>
					</div>

					<!-- Value Badge -->
					<div
						class="mb-8 inline-flex items-center rounded-full border border-white/20 bg-white/10 px-6 py-3 backdrop-blur-md"
					>
						<span class="text-lg font-bold text-white">💎 UNBEATABLE VALUE</span>
					</div>

					<!-- Main Title -->
					<h1 class="mb-8 text-6xl leading-none font-black text-white md:text-8xl lg:text-9xl">
						<span class="block">CHOOSE YOUR</span>
						<span
							class="block bg-gradient-to-r from-white via-gray-200 to-gray-400 bg-clip-text text-transparent"
						>
							POWER PLAN
						</span>
					</h1>

					<!-- Subtitle -->
					<p class="mx-auto mb-12 max-w-4xl text-xl leading-relaxed text-gray-300 md:text-2xl">
						Flexible membership options designed to fit your lifestyle and goals.
						<span class="font-semibold text-white">
							No hidden fees, no long-term contracts, just transparent pricing for premium fitness.
						</span>
					</p>

					<!-- Value Propositions -->
					<div class="mx-auto mb-16 grid max-w-5xl grid-cols-1 gap-8 md:grid-cols-3">
						<div
							class="transform transition-all delay-500 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-4 text-4xl">🔓</div>
							<h3 class="mb-2 text-lg font-bold text-white">No Lock-In Contracts</h3>
							<p class="text-gray-300">Cancel anytime with 30 days notice</p>
						</div>
						<div
							class="transform transition-all delay-600 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-4 text-4xl">💯</div>
							<h3 class="mb-2 text-lg font-bold text-white">100% Transparent</h3>
							<p class="text-gray-300">What you see is what you pay</p>
						</div>
						<div
							class="transform transition-all delay-700 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-4 text-4xl">🎯</div>
							<h3 class="mb-2 text-lg font-bold text-white">Best Value Guarantee</h3>
							<p class="text-gray-300">Premium facilities at competitive prices</p>
						</div>
					</div>

					<!-- CTA Buttons -->
					<div
						class="mb-24 flex transform flex-col gap-4 transition-all delay-900 duration-1000 sm:flex-row sm:justify-center {isVisible
							? 'translate-y-0 opacity-100'
							: 'translate-y-8 opacity-0'}"
					>
						<button
							class="group relative overflow-hidden rounded-2xl bg-white px-10 py-5 text-xl font-bold text-black transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-white/25"
						>
							<span class="relative z-10">START 7-DAY FREE TRIAL</span>
							<div
								class="absolute inset-0 translate-x-full transform bg-black transition-transform duration-300 group-hover:translate-x-0"
							></div>
							<span
								class="absolute inset-0 z-10 flex items-center justify-center text-xl font-bold text-white opacity-0 transition-opacity duration-300 group-hover:opacity-100"
							>
								START 7-DAY FREE TRIAL
							</span>
						</button>

						<button
							class="flex items-center justify-center gap-4 rounded-2xl border-2 border-white bg-transparent px-10 py-5 text-xl font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
						>
							<span>VIEW ALL PLANS</span>
							<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M19 9l-7 7-7-7"
								/>
							</svg>
						</button>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Pricing Preview -->
	<div class="absolute bottom-24 left-1/2 -translate-x-1/2 transform">
		<div
			class="flex items-center space-x-8 rounded-2xl border border-white/10 bg-white/5 px-8 py-4 backdrop-blur-md transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-4 opacity-0'}"
		>
			<!-- Popular Plans Preview -->
			<div class="flex items-center space-x-6">
				<div class="text-center">
					<div class="text-sm font-medium text-gray-400">Basic</div>
					<div class="text-xl font-bold text-white">$29/mo</div>
				</div>

				<div class="h-8 w-px bg-white/20"></div>

				<div class="text-center">
					<div class="text-sm font-medium text-gray-400">Premium</div>
					<div class="text-xl font-bold text-white">$59/mo</div>
					<div class="text-xs text-green-400">Most Popular</div>
				</div>

				<div class="h-8 w-px bg-white/20"></div>

				<div class="text-center">
					<div class="text-sm font-medium text-gray-400">Elite</div>
					<div class="text-xl font-bold text-white">$99/mo</div>
				</div>
			</div>

			<div class="h-8 w-px bg-white/20"></div>

			<!-- Special Offer -->
			<div class="flex items-center space-x-2">
				<div class="flex h-3 w-3 animate-pulse rounded-full bg-green-400"></div>
				<span class="text-sm font-medium text-white">Limited: 50% off first month</span>
			</div>
		</div>
	</div>

	<!-- Background Decorative Elements -->
	<div class="absolute top-20 right-12 h-40 w-40 rounded-full bg-white/5 blur-xl"></div>
	<div class="absolute right-4 bottom-40 h-32 w-32 rounded-full bg-white/10 blur-xl"></div>
	<div class="absolute bottom-32 left-12 h-48 w-48 rounded-full bg-white/5 blur-xl"></div>
</section>
