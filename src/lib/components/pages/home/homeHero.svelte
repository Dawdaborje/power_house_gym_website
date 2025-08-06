<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let mousePosition = { x: 0, y: 0 };
	let scrollY = 0;
	let currentSlide = 0;

	const heroSlides = [
		{
			image:
				'https://images.unsplash.com/photo-1534438327276-14e5300c3a48?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80',
			title: 'UNLEASH YOUR',
			subtitle: 'INNER BEAST',
			description: 'Transform your body, elevate your mind, dominate your goals'
		},
		{
			image:
				'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80',
			title: 'POWER THROUGH',
			subtitle: 'EVERY LIMIT',
			description: 'Where champions are forged and legends are born'
		},
		{
			image:
				'https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80',
			title: 'STRENGTH IS',
			subtitle: 'EVERYTHING',
			description: 'Join the elite community of Power House athletes'
		}
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);

		const handleMouseMove = (e: MouseEvent) => {
			mousePosition.x = e.clientX;
			mousePosition.y = e.clientY;
		};

		const handleScroll = () => {
			scrollY = window.scrollY;
		};

		window.addEventListener('mousemove', handleMouseMove);
		window.addEventListener('scroll', handleScroll);

		// Auto-cycle slides
		const slideInterval = setInterval(() => {
			currentSlide = (currentSlide + 1) % heroSlides.length;
		}, 6000);

		return () => {
			window.removeEventListener('mousemove', handleMouseMove);
			window.removeEventListener('scroll', handleScroll);
			clearInterval(slideInterval);
		};
	});

	function setSlide(index: number) {
		currentSlide = index;
	}
</script>

<section class="relative min-h-screen overflow-hidden bg-black">
	<!-- Dynamic Background Slideshow -->
	<div class="absolute inset-0">
		{#each heroSlides as slide, index}
			<div
				class="absolute inset-0 transition-opacity duration-1000 {currentSlide === index
					? 'opacity-100'
					: 'opacity-0'}"
			>
				<!-- Background Image with Parallax -->
				<div
					class="absolute inset-0 bg-cover bg-center bg-no-repeat transition-transform duration-75"
					style="background-image: url('{slide.image}'); 
					transform: translateY({scrollY * 0.3}px) scale(1.1);"
				></div>
			</div>
		{/each}

		<!-- Dynamic Overlay -->
		<div class="absolute inset-0 bg-black/60"></div>
		<div class="absolute inset-0 bg-gradient-to-br from-black/40 via-transparent to-black/60"></div>

		<!-- Animated mesh gradient -->
		<div
			class="absolute inset-0 opacity-20"
			style="background: radial-gradient(circle at {mousePosition.x / 25}% {mousePosition.y / 25}%, 
				rgba(255, 255, 255, 0.1) 0%, 
				rgba(255, 255, 255, 0.05) 30%, 
				transparent 70%)"
		></div>

		<!-- Geometric Pattern Overlay -->
		<div class="absolute inset-0 opacity-10">
			<svg class="h-full w-full" xmlns="http://www.w3.org/2000/svg">
				<defs>
					<pattern id="grid" width="60" height="60" patternUnits="userSpaceOnUse">
						<path d="M 60 0 L 0 0 0 60" fill="none" stroke="white" stroke-width="1" />
					</pattern>
				</defs>
				<rect width="100%" height="100%" fill="url(#grid)" />
			</svg>
		</div>
	</div>

	<!-- Hero Content -->
	<div class="relative z-10 flex min-h-screen items-center">
		<div class="mx-auto w-full max-w-7xl px-4 sm:px-6 lg:px-8">
			<div class="grid grid-cols-1 items-center gap-16 lg:grid-cols-12">
				<!-- Main Content -->
				<div class="lg:col-span-7">
					<div
						class="transform transition-all delay-300 duration-1000 {isVisible
							? 'translate-y-0 opacity-100'
							: 'translate-y-12 opacity-0'}"
					>
						<!-- Power House Branding -->
						<div class="mb-8 flex items-center space-x-4">
							<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
								<span class="text-2xl font-black text-black">PH</span>
							</div>
							<div>
								<div class="text-xl font-bold text-white">POWER HOUSE</div>
								<div class="text-sm text-gray-300">ELITE FITNESS</div>
							</div>
						</div>

						<!-- Dynamic Title -->
						<div class="mb-8">
							<h1 class="text-6xl leading-none font-black text-white md:text-8xl lg:text-9xl">
								<span class="block">{heroSlides[currentSlide].title}</span>
								<span
									class="block bg-gradient-to-r from-white via-gray-200 to-gray-400 bg-clip-text text-transparent"
								>
									{heroSlides[currentSlide].subtitle}
								</span>
							</h1>
						</div>

						<!-- Description -->
						<p class="mb-12 text-xl leading-relaxed text-gray-300 md:text-2xl lg:max-w-2xl">
							{heroSlides[currentSlide].description}
						</p>

						<!-- CTA Buttons -->
						<div class="mb-16 flex flex-col gap-4 sm:flex-row">
							<button
								class="group relative overflow-hidden rounded-2xl bg-white px-10 py-5 text-xl font-bold text-black transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-white/25"
							>
								<span class="relative z-10">START YOUR JOURNEY</span>
								<div
									class="absolute inset-0 translate-x-full transform bg-black transition-transform duration-300 group-hover:translate-x-0"
								></div>
								<span
									class="absolute inset-0 z-10 flex items-center justify-center text-xl font-bold text-white opacity-0 transition-opacity duration-300 group-hover:opacity-100"
								>
									START YOUR JOURNEY
								</span>
							</button>

							<button
								class="group flex items-center gap-4 rounded-2xl border-2 border-white bg-transparent px-10 py-5 text-xl font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
							>
								<span>WATCH STORY</span>
								<div
									class="flex h-12 w-12 items-center justify-center rounded-full bg-white/20 transition-all duration-300 group-hover:scale-110 group-hover:bg-black"
								>
									<svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
										<path
											d="M8 6.82v10.36c0 .79.87 1.27 1.54.84l8.14-5.18c.62-.39.62-1.29 0-1.68L9.54 5.98C8.87 5.55 8 6.03 8 6.82z"
										/>
									</svg>
								</div>
							</button>
						</div>

						<!-- Quick Stats -->
						<div class="grid grid-cols-3 gap-8">
							<div class="text-center">
								<div class="mb-2 text-4xl font-black text-white md:text-5xl">2K+</div>
								<div class="text-sm tracking-wider text-gray-400 uppercase">Members</div>
							</div>
							<div class="text-center">
								<div class="mb-2 text-4xl font-black text-white md:text-5xl">24/7</div>
								<div class="text-sm tracking-wider text-gray-400 uppercase">Access</div>
							</div>
							<div class="text-center">
								<div class="mb-2 text-4xl font-black text-white md:text-5xl">15+</div>
								<div class="text-sm tracking-wider text-gray-400 uppercase">Trainers</div>
							</div>
						</div>
					</div>
				</div>

				<!-- Right Side Content -->
				<div class="lg:col-span-5">
					<div
						class="transform transition-all delay-700 duration-1000 {isVisible
							? 'translate-y-0 opacity-100'
							: 'translate-y-12 opacity-0'}"
					>
						<!-- Achievement Card -->
						<div class="rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md">
							<div class="mb-6 flex items-center justify-between">
								<h3 class="text-2xl font-bold text-white">TODAY'S CHALLENGE</h3>
								<div class="rounded-full bg-green-500 px-3 py-1 text-sm font-bold text-white">
									LIVE
								</div>
							</div>

							<div class="mb-6">
								<div class="mb-2 text-4xl font-black text-white">BEAST MODE</div>
								<div class="text-gray-300">High-Intensity Strength Training</div>
							</div>

							<div class="mb-6">
								<div class="mb-3 flex justify-between text-sm">
									<span class="text-gray-400">Progress</span>
									<span class="text-white">68% Complete</span>
								</div>
								<div class="h-2 w-full rounded-full bg-white/20">
									<div class="h-2 w-2/3 rounded-full bg-gradient-to-r from-white to-gray-300"></div>
								</div>
							</div>

							<div class="grid grid-cols-2 gap-4">
								<div class="text-center">
									<div class="text-2xl font-bold text-white">47</div>
									<div class="text-xs text-gray-400">Active Now</div>
								</div>
								<div class="text-center">
									<div class="text-2xl font-bold text-white">156</div>
									<div class="text-xs text-gray-400">Today's Total</div>
								</div>
							</div>
						</div>

						<!-- Slide Navigation -->
						<div class="mt-8 flex justify-center space-x-3">
							{#each heroSlides as _, index}
								<button
									on:click={() => setSlide(index)}
									class="h-2 w-8 rounded-full transition-all duration-300 {currentSlide === index
										? 'bg-white'
										: 'bg-white/30'}"
								></button>
							{/each}
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Floating Action Elements -->
	<div class="absolute top-1/2 left-8 -translate-y-1/2 transform">
		<div class="flex flex-col space-y-4">
			<div
				class="flex h-14 w-14 items-center justify-center rounded-full bg-white/10 backdrop-blur-md transition-all duration-300 hover:bg-white/20"
			>
				<svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z"
					/>
				</svg>
			</div>
			<div
				class="flex h-14 w-14 items-center justify-center rounded-full bg-white/10 backdrop-blur-md transition-all duration-300 hover:bg-white/20"
			>
				<svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
					/>
				</svg>
			</div>
		</div>
	</div>

	<!-- Enhanced Scroll Indicator -->
	<div
		class="absolute bottom-8 left-1/2 -translate-x-1/2 transform transition-all delay-1000 duration-1000 {isVisible
			? 'translate-y-0 opacity-100'
			: 'translate-y-4 opacity-0'}"
	>
		<div class="flex flex-col items-center">
			<div class="mb-4 text-xs font-medium tracking-widest text-white/60 uppercase">
				Scroll to Explore
			</div>
			<div class="animate-bounce">
				<svg class="h-8 w-6 text-white/60" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M19 14l-7 7m0 0l-7-7m7 7V3"
					/>
				</svg>
			</div>
		</div>
	</div>

	<!-- Background Decorative Elements -->
	<div class="absolute top-24 right-16 h-32 w-32 rounded-full bg-white/5 blur-xl"></div>
	<div class="absolute right-8 bottom-32 h-24 w-24 rounded-full bg-white/10 blur-xl"></div>
	<div class="absolute bottom-40 left-16 h-40 w-40 rounded-full bg-white/5 blur-xl"></div>
</section>

<style>
	@keyframes bounce {
		0%,
		100% {
			transform: translateY(0);
		}
		50% {
			transform: translateY(-10px);
		}
	}

	.animate-bounce {
		animation: bounce 2s infinite;
	}

	/* Custom scrollbar styling */
	:global(body) {
		scrollbar-width: thin;
		scrollbar-color: rgba(255, 255, 255, 0.5) transparent;
	}

	:global(body::-webkit-scrollbar) {
		width: 6px;
	}

	:global(body::-webkit-scrollbar-track) {
		background: transparent;
	}

	:global(body::-webkit-scrollbar-thumb) {
		background: rgba(255, 255, 255, 0.5);
		border-radius: 3px;
	}
</style>
