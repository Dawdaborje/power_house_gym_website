<script lang="ts">
	import { onMount } from 'svelte';

	let sectionRef: HTMLElement;
	let isVisible = false;

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

		return () => {
			if (sectionRef) {
				observer.unobserve(sectionRef);
			}
		};
	});
</script>

<section bind:this={sectionRef} class="relative overflow-hidden bg-black py-24">
	<!-- Background Pattern -->
	<div class="absolute inset-0 opacity-5">
		<div
			class="absolute inset-0"
			style="background-image: radial-gradient(circle at 2px 2px, rgba(255,255,255,0.3) 1px, transparent 0); background-size: 50px 50px;"
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
					<span class="text-sm font-medium text-white/70">💪 Why Choose Us</span>
				</div>

				<h2 class="mb-6 text-5xl font-black text-white md:text-6xl lg:text-7xl">
					WHY <span
						class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
						>POWER HOUSE</span
					>
				</h2>

				<p class="mx-auto max-w-3xl text-xl leading-relaxed text-gray-300 md:text-2xl">
					We're not just another gym. We're your transformation partner,
					<span class="font-semibold text-white">committed to your success.</span>
				</p>
			</div>
		</div>

		<!-- Main Benefits Grid -->
		<div class="mb-20 grid grid-cols-1 gap-16 lg:grid-cols-2">
			<!-- Left Column - Primary Benefits -->
			<div class="space-y-12">
				<!-- State-of-the-Art Equipment -->
				<div
					class="transform transition-all delay-400 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-8 opacity-0'}"
				>
					<div class="flex items-start space-x-6">
						<div class="flex-shrink-0">
							<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
								<svg
									class="h-8 w-8 text-black"
									fill="none"
									stroke="currentColor"
									viewBox="0 0 24 24"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										stroke-width="2"
										d="M13 10V3L4 14h7v7l9-11h-7z"
									/>
								</svg>
							</div>
						</div>
						<div class="flex-1">
							<h3 class="mb-3 text-2xl font-bold text-white">Premium Equipment</h3>
							<p class="text-lg leading-relaxed text-gray-300">
								Access to the latest fitness technology and equipment from industry leaders. Our
								machines are regularly maintained and updated to ensure peak performance.
							</p>
						</div>
					</div>
				</div>

				<!-- Expert Trainers -->
				<div
					class="transform transition-all delay-600 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-8 opacity-0'}"
				>
					<div class="flex items-start space-x-6">
						<div class="flex-shrink-0">
							<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
								<svg
									class="h-8 w-8 text-black"
									fill="none"
									stroke="currentColor"
									viewBox="0 0 24 24"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										stroke-width="2"
										d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197m13.5-9a2.5 2.5 0 11-5 0 2.5 2.5 0 015 0z"
									/>
								</svg>
							</div>
						</div>
						<div class="flex-1">
							<h3 class="mb-3 text-2xl font-bold text-white">Expert Guidance</h3>
							<p class="text-lg leading-relaxed text-gray-300">
								Our certified trainers bring years of experience and proven results. Get
								personalized workout plans and nutrition guidance tailored to your goals.
							</p>
						</div>
					</div>
				</div>

				<!-- Community -->
				<div
					class="transform transition-all delay-800 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-8 opacity-0'}"
				>
					<div class="flex items-start space-x-6">
						<div class="flex-shrink-0">
							<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
								<svg
									class="h-8 w-8 text-black"
									fill="none"
									stroke="currentColor"
									viewBox="0 0 24 24"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										stroke-width="2"
										d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 919.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"
									/>
								</svg>
							</div>
						</div>
						<div class="flex-1">
							<h3 class="mb-3 text-2xl font-bold text-white">Supportive Community</h3>
							<p class="text-lg leading-relaxed text-gray-300">
								Join a community of motivated individuals who share your passion for fitness. Find
								workout partners, join group classes, and celebrate achievements together.
							</p>
						</div>
					</div>
				</div>
			</div>

			<!-- Right Column - Visual Element -->
			<div
				class="transform transition-all delay-1000 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="relative">
					<!-- Main Image Container -->
					<div
						class="relative h-96 min-h-[500px] overflow-hidden rounded-3xl bg-gradient-to-br from-gray-100 to-gray-200 lg:h-full"
					>
						<img
							src="https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80"
							alt="Power House Gym Interior"
							class="h-full w-full object-cover"
						/>

						<!-- Overlay -->
						<div class="absolute inset-0 bg-black/20"></div>

						<!-- Stats Overlay -->
						<div class="absolute right-6 bottom-6 left-6">
							<div class="rounded-2xl bg-white/95 p-6 backdrop-blur-md">
								<div class="grid grid-cols-2 gap-4">
									<div class="text-center">
										<div class="text-2xl font-bold text-black">98%</div>
										<div class="text-sm text-gray-600">Success Rate</div>
									</div>
									<div class="text-center">
										<div class="text-2xl font-bold text-black">5★</div>
										<div class="text-sm text-gray-600">Average Rating</div>
									</div>
								</div>
							</div>
						</div>
					</div>

					<!-- Floating Elements -->
					<div
						class="absolute -top-4 -right-4 flex h-20 w-20 items-center justify-center rounded-full bg-white"
					>
						<span class="text-lg font-bold text-black">#1</span>
					</div>
				</div>
			</div>
		</div>

		<!-- Secondary Benefits -->
		<div
			class="transform transition-all delay-1200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="grid grid-cols-1 gap-8 md:grid-cols-3">
				<!-- 24/7 Access -->
				<div
					class="rounded-3xl border border-white/10 bg-white/5 p-8 text-center transition-colors duration-300 hover:bg-white/10"
				>
					<div class="mx-auto mb-6 flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
						<svg class="h-8 w-8 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
							/>
						</svg>
					</div>
					<h4 class="mb-3 text-xl font-bold text-white">24/7 Access</h4>
					<p class="text-gray-300">
						Work out on your schedule. Our gym is open round the clock for ultimate flexibility.
					</p>
				</div>

				<!-- Clean & Safe -->
				<div
					class="rounded-3xl border border-white/10 bg-white/5 p-8 text-center transition-colors duration-300 hover:bg-white/10"
				>
					<div class="mx-auto mb-6 flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
						<svg class="h-8 w-8 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
							/>
						</svg>
					</div>
					<h4 class="mb-3 text-xl font-bold text-white">Clean & Safe</h4>
					<p class="text-gray-300">
						Maintained to the highest hygiene standards with regular deep cleaning and sanitization.
					</p>
				</div>

				<!-- Affordable Plans -->
				<div
					class="rounded-3xl border border-white/10 bg-white/5 p-8 text-center transition-colors duration-300 hover:bg-white/10"
				>
					<div class="mx-auto mb-6 flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
						<svg class="h-8 w-8 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1"
							/>
						</svg>
					</div>
					<h4 class="mb-3 text-xl font-bold text-white">Flexible Plans</h4>
					<p class="text-gray-300">
						Choose from various membership options designed to fit your budget and commitment level.
					</p>
				</div>
			</div>
		</div>

		<!-- Call to Action -->
		<div
			class="mt-16 transform text-center transition-all delay-1400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="inline-flex flex-col gap-4 sm:flex-row">
				<button
					class="rounded-2xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
				>
					Start Your Free Trial
				</button>
				<button
					class="rounded-2xl border-2 border-white px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
				>
					Schedule a Tour
				</button>
			</div>
		</div>
	</div>
</section>

<style>
	/* Additional smooth animations for intersection observer */
	.transform {
		transition-property: transform, opacity;
		transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
	}
</style>
