<script lang="ts">
	import { onMount } from 'svelte';

	let sectionRef: HTMLElement;
	let isVisible = false;

	const programs = [
		{
			id: 'strength',
			title: 'STRENGTH',
			subtitle: 'Build Power',
			description:
				'Functional strength training with compound movements designed to build muscle, increase power, and enhance overall performance.',
			icon: 'dumbbell',
			image:
				'https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80',
			features: [
				'Compound Movements',
				'Progressive Overload',
				'Muscle Building',
				'Power Development'
			]
		},
		{
			id: 'cardio',
			title: 'CARDIO',
			subtitle: 'Burn & Condition',
			description:
				'High-intensity cardiovascular workouts that torch calories, improve endurance, and boost your metabolic rate.',
			icon: 'heart',
			image:
				'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80',
			features: ['HIIT Training', 'Fat Burning', 'Endurance Building', 'Heart Health']
		},
		{
			id: 'hybrid',
			title: 'HYBRID',
			subtitle: 'Best of Both',
			description:
				'Perfect combination of strength and cardio training for complete functional fitness and body transformation.',
			icon: 'lightning',
			image:
				'https://images.unsplash.com/photo-1534438327276-14e5300c3a48?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80',
			features: [
				'Strength + Cardio',
				'Functional Fitness',
				'Body Transformation',
				'Complete Conditioning'
			]
		}
	];

	let activeProgram = 0;

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						isVisible = true;
					}
				});
			},
			{ threshold: 0.1 }
		);

		if (sectionRef) {
			observer.observe(sectionRef);
		}

		// Auto-cycle through programs
		const interval = setInterval(() => {
			activeProgram = (activeProgram + 1) % programs.length;
		}, 5000);

		return () => {
			if (sectionRef) {
				observer.unobserve(sectionRef);
			}
			clearInterval(interval);
		};
	});

	function getIcon(iconType: string) {
		switch (iconType) {
			case 'dumbbell':
				return 'M21 12.1c.9 0 1.6.7 1.6 1.6v.6c0 .9-.7 1.6-1.6 1.6h-1.4c-.4 0-.8-.2-1.1-.4l-1.8-1.4c-.4-.3-.6-.8-.6-1.3v-1.2c0-.5.2-1 .6-1.3l1.8-1.4c.3-.2.7-.4 1.1-.4H21zm-18 0h1.4c.4 0 .8.2 1.1.4l1.8 1.4c.4.3.6.8.6 1.3v1.2c0 .5-.2 1-.6 1.3l-1.8 1.4c-.3.2-.7.4-1.1.4H3c-.9 0-1.6-.7-1.6-1.6v-.6c0-.9.7-1.6 1.6-1.6z';
			case 'heart':
				return 'M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z';
			case 'lightning':
				return 'M13 2L3 14h9l-1 8 10-12h-9l1-8z';
			default:
				return 'M13 2L3 14h9l-1 8 10-12h-9l1-8z';
		}
	}
</script>

<section bind:this={sectionRef} class="relative overflow-hidden bg-black py-24">
	<!-- Background Elements -->
	<div class="absolute inset-0 opacity-5">
		<div
			class="absolute inset-0"
			style="background-image: radial-gradient(circle at 2px 2px, rgba(255,255,255,0.3) 1px, transparent 0); background-size: 60px 60px;"
		></div>
	</div>

	<div class="relative z-10 mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<!-- Section Header -->
		<div class="mb-20 text-center">
			<div
				class="transform transition-all delay-200 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div
					class="mb-6 inline-flex items-center rounded-full border border-white/10 bg-white/5 px-6 py-2"
				>
					<span class="text-sm font-medium text-white/70">🔥 Our Programs</span>
				</div>

				<h2 class="mb-6 text-5xl font-black text-white md:text-6xl lg:text-7xl">
					CHOOSE YOUR <span
						class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
						>PROGRAM</span
					>
				</h2>

				<p class="mx-auto max-w-3xl text-xl leading-relaxed text-gray-300 md:text-2xl">
					Every workout is designed for every body. Find your perfect fit and
					<span class="font-semibold text-white">transform the way you train.</span>
				</p>
			</div>
		</div>

		<!-- Programs Grid -->
		<div class="grid grid-cols-1 items-center gap-16 lg:grid-cols-2">
			<!-- Program Selection -->
			<div
				class="transform space-y-6 transition-all delay-400 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				{#each programs as program, index}
					<button
						class="w-full rounded-3xl border border-white/10 bg-white/5 p-6 text-left transition-all duration-300 hover:bg-white/10 {activeProgram ===
						index
							? 'border-white/20 bg-white/15'
							: ''}"
						on:click={() => (activeProgram = index)}
					>
						<div class="flex items-start space-x-6">
							<div class="flex-shrink-0">
								<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
									<svg class="h-8 w-8 text-black" fill="currentColor" viewBox="0 0 24 24">
										<path d={getIcon(program.icon)} />
									</svg>
								</div>
							</div>
							<div class="flex-1">
								<div class="mb-2 flex items-center space-x-3">
									<h3 class="text-2xl font-bold text-white">{program.title}</h3>
									<span class="text-lg text-gray-400">{program.subtitle}</span>
								</div>
								<p class="mb-4 leading-relaxed text-gray-300">
									{program.description}
								</p>
								<div class="flex flex-wrap gap-2">
									{#each program.features as feature}
										<span class="rounded-full bg-white/10 px-3 py-1 text-sm text-white/80">
											{feature}
										</span>
									{/each}
								</div>
							</div>
						</div>
					</button>
				{/each}
			</div>

			<!-- Program Visual -->
			<div
				class="transform transition-all delay-600 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="relative">
					<!-- Main Image -->
					<div class="relative h-96 overflow-hidden rounded-3xl lg:h-[600px]">
						<img
							src={programs[activeProgram].image}
							alt={programs[activeProgram].title}
							class="h-full w-full object-cover transition-all duration-700"
						/>

						<!-- Overlay -->
						<div class="absolute inset-0 bg-black/40"></div>

						<!-- Program Info Overlay -->
						<div class="absolute right-8 bottom-8 left-8">
							<div class="rounded-2xl bg-white/95 p-6 backdrop-blur-md">
								<div class="flex items-center justify-between">
									<div>
										<h4 class="mb-1 text-2xl font-bold text-black">
											{programs[activeProgram].title}
										</h4>
										<p class="text-gray-600">
											{programs[activeProgram].subtitle}
										</p>
									</div>
									<div class="flex h-12 w-12 items-center justify-center rounded-xl bg-black">
										<svg class="h-6 w-6 text-white" fill="currentColor" viewBox="0 0 24 24">
											<path d={getIcon(programs[activeProgram].icon)} />
										</svg>
									</div>
								</div>
							</div>
						</div>
					</div>

					<!-- Program Indicators -->
					<div class="mt-8 flex justify-center space-x-3">
						{#each programs as _, index}
							<button
								class="h-3 w-3 rounded-full transition-all duration-300 {activeProgram === index
									? 'bg-white'
									: 'bg-white/30'}"
								on:click={() => (activeProgram = index)}
							></button>
						{/each}
					</div>
				</div>
			</div>
		</div>

		<!-- Call to Action -->
		<div
			class="mt-20 transform text-center transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="inline-flex flex-col gap-4 sm:flex-row">
				<button
					class="rounded-2xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
				>
					Book Your First Class
				</button>
				<button
					class="rounded-2xl border-2 border-white px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
				>
					View Class Schedule
				</button>
			</div>
		</div>
	</div>
</section>

<style>
	/* Smooth transitions for program switching */
	img {
		transition: opacity 0.7s ease-in-out;
	}
</style>
