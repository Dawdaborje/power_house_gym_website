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

<section class="relative min-h-[80vh] overflow-hidden bg-black">
	<!-- Background Image with Parallax -->
	<div class="absolute inset-0">
		<div
			class="absolute inset-0 bg-cover bg-center bg-no-repeat transition-transform duration-75"
			style="background-image: url('https://images.unsplash.com/photo-1534438327276-14e5300c3a48?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80'); 
			transform: translateY({scrollY * 0.3}px) scale(1.1);"
		></div>

		<!-- Overlay -->
		<div class="absolute inset-0 bg-black/70"></div>
		<div class="absolute inset-0 bg-gradient-to-br from-black/60 via-transparent to-black/80"></div>
	</div>

	<!-- Geometric Pattern Overlay -->
	<div class="absolute inset-0 opacity-10">
		<svg class="h-full w-full" xmlns="http://www.w3.org/2000/svg">
			<defs>
				<pattern id="programs-grid" width="60" height="60" patternUnits="userSpaceOnUse">
					<path d="M 60 0 L 0 0 0 60" fill="none" stroke="white" stroke-width="1" />
				</pattern>
			</defs>
			<rect width="100%" height="100%" fill="url(#programs-grid)" />
		</svg>
	</div>

	<!-- Hero Content -->
	<div class="relative z-10 flex min-h-[80vh] items-center">
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
						<span class="text-white">Programs</span>
					</div>

					<!-- Main Title -->
					<h1 class="mb-8 text-6xl leading-none font-black text-white md:text-8xl lg:text-9xl">
						<span class="block">TRANSFORM</span>
						<span
							class="block bg-gradient-to-r from-white via-gray-200 to-gray-400 bg-clip-text text-transparent"
						>
							YOUR LIMITS
						</span>
					</h1>

					<!-- Subtitle -->
					<p class="mx-auto mb-12 max-w-4xl text-xl leading-relaxed text-gray-300 md:text-2xl">
						Discover our comprehensive range of fitness programs designed to challenge every body
						type, fitness level, and goal. From strength training to high-intensity cardio,
						<span class="font-semibold text-white"
							>find your perfect workout and push beyond what you thought possible.</span
						>
					</p>

					<!-- Program Stats -->
					<div class="mx-auto mb-16 grid max-w-4xl grid-cols-2 gap-8 md:grid-cols-4">
						<div
							class="transform transition-all delay-500 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-2 text-4xl font-black text-white md:text-5xl">15+</div>
							<div class="text-sm tracking-wider text-gray-400 uppercase">Programs</div>
						</div>
						<div
							class="transform transition-all delay-600 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-2 text-4xl font-black text-white md:text-5xl">50+</div>
							<div class="text-sm tracking-wider text-gray-400 uppercase">Classes/Week</div>
						</div>
						<div
							class="transform transition-all delay-700 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-2 text-4xl font-black text-white md:text-5xl">12</div>
							<div class="text-sm tracking-wider text-gray-400 uppercase">Expert Trainers</div>
						</div>
						<div
							class="transform transition-all delay-800 duration-1000 {isVisible
								? 'translate-y-0 opacity-100'
								: 'translate-y-8 opacity-0'}"
						>
							<div class="mb-2 text-4xl font-black text-white md:text-5xl">24/7</div>
							<div class="text-sm tracking-wider text-gray-400 uppercase">Access</div>
						</div>
					</div>

					<!-- CTA Buttons -->
					<div
						class="flex transform flex-col gap-4 transition-all delay-900 duration-1000 sm:flex-row sm:justify-center {isVisible
							? 'translate-y-0 opacity-100'
							: 'translate-y-8 opacity-0'}"
					>
						<button
							class="group relative overflow-hidden rounded-2xl bg-white px-10 py-5 text-xl font-bold text-black transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-white/25"
						>
							<span class="relative z-10">EXPLORE PROGRAMS</span>
							<div
								class="absolute inset-0 translate-x-full transform bg-black transition-transform duration-300 group-hover:translate-x-0"
							></div>
							<span
								class="absolute inset-0 z-10 flex items-center justify-center text-xl font-bold text-white opacity-0 transition-opacity duration-300 group-hover:opacity-100"
							>
								EXPLORE PROGRAMS
							</span>
						</button>

						<button
							class="flex items-center justify-center gap-4 rounded-2xl border-2 border-white bg-transparent px-10 py-5 text-xl font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
						>
							<span>VIEW SCHEDULE</span>
							<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
								/>
							</svg>
						</button>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Quick Navigation -->
	<div class="absolute bottom-8 left-1/2 -translate-x-1/2 transform">
		<div
			class="flex items-center space-x-8 rounded-2xl border border-white/10 bg-white/5 px-8 py-4 backdrop-blur-md transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-4 opacity-0'}"
		>
			<a
				href="#strength"
				class="flex items-center space-x-2 text-white/70 transition-colors hover:text-white"
			>
				<div class="h-2 w-2 rounded-full bg-white/70"></div>
				<span class="text-sm font-medium">Strength</span>
			</a>
			<a
				href="#cardio"
				class="flex items-center space-x-2 text-white/70 transition-colors hover:text-white"
			>
				<div class="h-2 w-2 rounded-full bg-white/70"></div>
				<span class="text-sm font-medium">Cardio</span>
			</a>
			<a
				href="#hiit"
				class="flex items-center space-x-2 text-white/70 transition-colors hover:text-white"
			>
				<div class="h-2 w-2 rounded-full bg-white/70"></div>
				<span class="text-sm font-medium">HIIT</span>
			</a>
			<a
				href="#recovery"
				class="flex items-center space-x-2 text-white/70 transition-colors hover:text-white"
			>
				<div class="h-2 w-2 rounded-full bg-white/70"></div>
				<span class="text-sm font-medium">Recovery</span>
			</a>
		</div>
	</div>

	<!-- Background Decorative Elements -->
	<div class="absolute top-24 right-16 h-32 w-32 rounded-full bg-white/5 blur-xl"></div>
	<div class="absolute right-8 bottom-32 h-24 w-24 rounded-full bg-white/10 blur-xl"></div>
	<div class="absolute bottom-40 left-16 h-40 w-40 rounded-full bg-white/5 blur-xl"></div>
</section>
