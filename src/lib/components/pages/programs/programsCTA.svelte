<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	const benefits = [
		{
			icon: '🎯',
			title: 'Personalized Approach',
			description: 'Every program is tailored to your fitness level and goals'
		},
		{
			icon: '⏰',
			title: 'Flexible Scheduling',
			description: 'Choose from 50+ classes per week at times that work for you'
		},
		{
			icon: '👥',
			title: 'Expert Guidance',
			description: 'Certified trainers provide professional support every step of the way'
		},
		{
			icon: '📈',
			title: 'Track Progress',
			description: 'Monitor your improvements with our comprehensive tracking system'
		}
	];

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
				<pattern id="cta-grid" width="60" height="60" patternUnits="userSpaceOnUse">
					<path d="M 60 0 L 0 0 0 60" fill="none" stroke="white" stroke-width="1" />
				</pattern>
			</defs>
			<rect width="100%" height="100%" fill="url(#cta-grid)" />
		</svg>
	</div>

	<div class="relative z-10 mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<!-- Main CTA Section -->
		<div
			class="mb-20 transform text-center transition-all delay-200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mb-8 inline-flex items-center rounded-full border border-white/10 bg-white/5 px-6 py-2"
			>
				<span class="text-sm font-medium text-white/70">🚀 Start Your Journey</span>
			</div>

			<h2 class="mb-6 text-5xl font-black text-white md:text-6xl lg:text-7xl">
				READY TO
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					TRANSFORM?
				</span>
			</h2>

			<p class="mx-auto mb-12 max-w-4xl text-xl leading-relaxed text-gray-300 md:text-2xl">
				Join thousands of members who have already transformed their lives at Power House.
				<span class="font-semibold text-white">Your strongest self is waiting.</span>
			</p>

			<!-- Main CTA Buttons -->
			<div class="mb-16 flex flex-col gap-6 sm:flex-row sm:justify-center">
				<button
					class="group relative overflow-hidden rounded-2xl bg-white px-12 py-6 text-xl font-bold text-black transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-white/25"
				>
					<span class="relative z-10">START FREE TRIAL</span>
					<div
						class="absolute inset-0 translate-x-full transform bg-black transition-transform duration-300 group-hover:translate-x-0"
					></div>
					<span
						class="absolute inset-0 z-10 flex items-center justify-center text-xl font-bold text-white opacity-0 transition-opacity duration-300 group-hover:opacity-100"
					>
						START FREE TRIAL
					</span>
				</button>

				<button
					class="flex items-center justify-center gap-4 rounded-2xl border-2 border-white bg-transparent px-12 py-6 text-xl font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
				>
					<span>SCHEDULE TOUR</span>
					<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"
						/>
					</svg>
				</button>
			</div>

			<!-- Trust Indicators -->
			<div
				class="flex flex-col items-center space-y-6 sm:flex-row sm:justify-center sm:space-y-0 sm:space-x-12"
			>
				<div class="flex items-center space-x-2">
					<div class="flex -space-x-2">
						<div class="h-10 w-10 rounded-full border-2 border-white bg-gray-300"></div>
						<div class="h-10 w-10 rounded-full border-2 border-white bg-gray-400"></div>
						<div class="h-10 w-10 rounded-full border-2 border-white bg-gray-500"></div>
					</div>
					<span class="font-medium text-white">2,000+ members</span>
				</div>
				<div class="flex items-center space-x-2">
					<div class="flex items-center">
						{#each Array(5) as _}
							<svg class="h-5 w-5 text-yellow-400" fill="currentColor" viewBox="0 0 24 24">
								<path
									d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
								/>
							</svg>
						{/each}
					</div>
					<span class="font-medium text-white">4.9/5 rating</span>
				</div>
			</div>
		</div>

		<!-- Benefits Grid -->
		<div
			class="mb-20 grid transform grid-cols-1 gap-8 transition-all delay-400 duration-1000 md:grid-cols-2 lg:grid-cols-4 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each benefits as benefit, index}
				<div
					class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md transition-all duration-300 hover:border-white/20 hover:bg-white/10"
					style="transition-delay: {index * 150}ms"
				>
					<div class="mb-4 text-4xl">{benefit.icon}</div>
					<h3 class="mb-3 text-lg font-bold text-white">{benefit.title}</h3>
					<p class="text-gray-300">{benefit.description}</p>
				</div>
			{/each}
		</div>

		<!-- Special Offer -->
		<div
			class="mx-auto max-w-4xl transform rounded-3xl border border-white/20 bg-gradient-to-r from-white/10 to-white/5 p-8 text-center backdrop-blur-md transition-all delay-600 duration-1000 md:p-12 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mb-6 inline-flex items-center rounded-full bg-red-500 px-6 py-2 text-white">
				<span class="text-sm font-bold">🔥 LIMITED TIME OFFER</span>
			</div>

			<h3 class="mb-4 text-4xl font-black text-white md:text-5xl">7 DAYS FREE TRIAL</h3>

			<p class="mb-8 text-xl text-gray-300">
				Experience all our programs, meet our trainers, and see why Power House is the right choice
				for you. No commitment, no hidden fees.
			</p>

			<div class="mb-8 grid grid-cols-1 gap-6 md:grid-cols-3">
				<div class="rounded-xl border border-white/10 bg-white/5 p-4">
					<div class="text-2xl font-bold text-white">✓</div>
					<div class="text-sm font-medium text-white">Access to All Programs</div>
				</div>
				<div class="rounded-xl border border-white/10 bg-white/5 p-4">
					<div class="text-2xl font-bold text-white">✓</div>
					<div class="text-sm font-medium text-white">Personal Training Session</div>
				</div>
				<div class="rounded-xl border border-white/10 bg-white/5 p-4">
					<div class="text-2xl font-bold text-white">✓</div>
					<div class="text-sm font-medium text-white">Fitness Assessment</div>
				</div>
			</div>

			<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
				<button
					class="rounded-2xl bg-white px-10 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
				>
					Claim Free Trial
				</button>
				<div class="text-sm text-white/70">
					<span class="font-semibold">No credit card required</span>
				</div>
			</div>
		</div>

		<!-- Contact Info -->
		<div
			class="mt-20 transform text-center transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h4 class="mb-6 text-2xl font-bold text-white">Questions? We're Here to Help</h4>
			<div
				class="flex flex-col items-center space-y-4 sm:flex-row sm:justify-center sm:space-y-0 sm:space-x-8"
			>
				<a
					href="tel:555-123-4567"
					class="flex items-center space-x-2 text-gray-300 transition-colors hover:text-white"
				>
					<svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
						/>
					</svg>
					<span>(555) 123-POWER</span>
				</a>
				<a
					href="mailto:info@powerhousegym.com"
					class="flex items-center space-x-2 text-gray-300 transition-colors hover:text-white"
				>
					<svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
						/>
					</svg>
					<span>info@powerhousegym.com</span>
				</a>
				<div class="flex items-center space-x-2 text-gray-300">
					<svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
						/>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
						/>
					</svg>
					<span>123 Fitness Street, Muscle City</span>
				</div>
			</div>
		</div>
	</div>

	<!-- Background Decorative Elements -->
	<div class="absolute top-24 right-16 h-32 w-32 rounded-full bg-white/5 blur-xl"></div>
	<div class="absolute right-8 bottom-32 h-24 w-24 rounded-full bg-white/10 blur-xl"></div>
	<div class="absolute bottom-40 left-16 h-40 w-40 rounded-full bg-white/5 blur-xl"></div>
</section>
