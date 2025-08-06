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

<section class="relative min-h-[90vh] overflow-hidden bg-black">
	<!-- Background Image with Parallax -->
	<div class="absolute inset-0">
		<div
			class="absolute inset-0 bg-cover bg-center bg-no-repeat transition-transform duration-75"
			style="background-image: url('https://images.unsplash.com/photo-1540497077202-7c8a3999166f?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80'); 
			transform: translateY({scrollY * 0.3}px) scale(1.1);"
		></div>
		
		<!-- Overlay -->
		<div class="absolute inset-0 bg-black/70"></div>
		<div class="absolute inset-0 bg-gradient-to-br from-black/80 via-transparent to-black/90"></div>
	</div>

	<!-- Geometric Pattern Overlay -->
	<div class="absolute inset-0 opacity-10">
		<svg class="h-full w-full" xmlns="http://www.w3.org/2000/svg">
			<defs>
				<pattern id="about-grid" width="100" height="100" patternUnits="userSpaceOnUse">
					<circle cx="50" cy="50" r="2" fill="white" opacity="0.4" />
					<circle cx="0" cy="0" r="1" fill="white" opacity="0.2" />
					<circle cx="100" cy="100" r="1" fill="white" opacity="0.2" />
				</pattern>
			</defs>
			<rect width="100%" height="100%" fill="url(#about-grid)" />
		</svg>
	</div>

	<!-- Hero Content -->
	<div class="relative z-10 flex min-h-[90vh] items-center">
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
						<span class="text-white">About Us</span>
					</div>

					<!-- Mission Badge -->
					<div
						class="mb-8 inline-flex items-center rounded-full border border-white/20 bg-white/10 px-6 py-3 backdrop-blur-md"
					>
						<span class="text-lg font-bold text-white">🏆 FORGING CHAMPIONS SINCE 2018</span>
					</div>

					<!-- Main Title -->
					<h1 class="mb-8 text-6xl leading-none font-black text-white md:text-8xl lg:text-9xl">
						<span class="block">WHERE LEGENDS</span>
						<span
							class="block bg-gradient-to-r from-white via-gray-200 to-gray-400 bg-clip-text text-transparent"
						>
							ARE BORN
						</span>
					</h1>

					<!-- Subtitle -->
					<p class="mx-auto mb-12 max-w-4xl text-xl leading-relaxed text-gray-300 md:text-2xl">
						More than just a gym - we're a community of dedicated athletes, passionate trainers, and
						visionaries who believe
						<span class="font-semibold text-white">
							every person has the power to achieve greatness.
						</span>
					</p>

					<!-- Key Stats -->
					<div class="mx-auto mb-16 grid max-w-5xl grid-cols-2 gap-8 md:grid-cols-4">
						<div
							class="transform transition-all delay-500 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-2 text-4xl font-black text-white md:text-5xl">6</div>
							<div class="text-sm tracking-wider text-gray-400 uppercase">Years of Excellence</div>
						</div>
						<div
							class="transform transition-all delay-600 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-2 text-4xl font-black text-white md:text-5xl">15K+</div>
							<div class="text-sm tracking-wider text-gray-400 uppercase">Lives Transformed</div>
						</div>
						<div
							class="transform transition-all delay-700 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-2 text-4xl font-black text-white md:text-5xl">50+</div>
							<div class="text-sm tracking-wider text-gray-400 uppercase">Expert Team Members</div>
						</div>
						<div
							class="transform transition-all delay-800 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-2 text-4xl font-black text-white md:text-5xl">24/7</div>
							<div class="text-sm tracking-wider text-gray-400 uppercase">Commitment to You</div>
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
							<span class="relative z-10">MEET OUR TEAM</span>
							<div
								class="absolute inset-0 translate-x-full transform bg-black transition-transform duration-300 group-hover:translate-x-0"
							></div>
							<span
								class="absolute inset-0 z-10 flex items-center justify-center text-xl font-bold text-white opacity-0 transition-opacity duration-300 group-hover:opacity-100"
							>
								MEET OUR TEAM
							</span>
						</button>

						<button
							class="flex items-center justify-center gap-4 rounded-2xl border-2 border-white bg-transparent px-10 py-5 text-xl font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
						>
							<span>OUR STORY</span>
							<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
							</svg>
						</button>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Founding Principles Preview -->
	<div class="absolute bottom-8 left-1/2 -translate-x-1/2 transform">
		<div
			class="flex items-center space-x-8 rounded-2xl border border-white/10 bg-white/5 px-8 py-4 backdrop-blur-md transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-4 opacity-0'}"
		>
			<!-- Core Values Preview -->
			<div class="flex items-center space-x-6">
				<div class="text-center">
					<div class="text-2xl">🎯</div>
					<div class="text-sm font-medium text-white">Excellence</div>
				</div>
				
				<div class="h-8 w-px bg-white/20"></div>
				
				<div class="text-center">
					<div class="text-2xl">🤝</div>
					<div class="text-sm font-medium text-white">Community</div>
				</div>
				
				<div class="h-8 w-px bg-white/20"></div>
				
				<div class="text-center">
					<div class="text-2xl">💪</div>
					<div class="text-sm font-medium text-white">Transformation</div>
				</div>

				<div class="h-8 w-px bg-white/20"></div>
				
				<div class="text-center">
					<div class="text-2xl">🚀</div>
					<div class="text-sm font-medium text-white">Innovation</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Background Decorative Elements -->
	<div class="absolute top-20 right-12 h-40 w-40 rounded-full bg-white/5 blur-xl"></div>
	<div class="absolute right-4 bottom-40 h-32 w-32 rounded-full bg-white/10 blur-xl"></div>
	<div class="absolute bottom-32 left-12 h-48 w-48 rounded-full bg-white/5 blur-xl"></div>
</section>