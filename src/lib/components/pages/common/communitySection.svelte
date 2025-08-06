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
					<span class="text-sm font-medium text-white/70">🤝 Community First</span>
				</div>

				<h2 class="mb-6 text-5xl font-black text-white md:text-6xl lg:text-7xl">
					MADE BY <span
						class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
						>COMMUNITY</span
					>
				</h2>

				<p class="mx-auto max-w-4xl text-xl leading-relaxed text-gray-300 md:text-2xl">
					At Power House, community is at the heart of everything we do. More than just a workout,
					<span class="font-semibold text-white"
						>we're a family driven by connection, support, and shared goals.</span
					>
				</p>
			</div>
		</div>

		<!-- Main Content Grid -->
		<div class="mb-20 grid grid-cols-1 items-center gap-16 lg:grid-cols-2">
			<!-- Community Image -->
			<div
				class="transform transition-all delay-400 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="relative">
					<div class="relative h-96 overflow-hidden rounded-3xl lg:h-[500px]">
						<img
							src="https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80"
							alt="Power House Community"
							class="h-full w-full object-cover"
						/>

						<!-- Overlay -->
						<div class="absolute inset-0 bg-black/30"></div>

						<!-- Community Stats Overlay -->
						<div class="absolute top-6 right-6 left-6">
							<div class="rounded-2xl bg-white/95 p-4 backdrop-blur-md">
								<div class="flex items-center justify-between">
									<div class="text-center">
										<div class="text-lg font-bold text-black">2,000+</div>
										<div class="text-xs text-gray-600">Members</div>
									</div>
									<div class="text-center">
										<div class="text-lg font-bold text-black">500+</div>
										<div class="text-xs text-gray-600">Classes/Month</div>
									</div>
									<div class="text-center">
										<div class="text-lg font-bold text-black">50+</div>
										<div class="text-xs text-gray-600">Events/Year</div>
									</div>
								</div>
							</div>
						</div>

						<!-- Live Activity Badge -->
						<div class="absolute bottom-6 left-6">
							<div
								class="flex items-center space-x-2 rounded-full bg-black/80 px-4 py-2 backdrop-blur-md"
							>
								<div class="h-2 w-2 animate-pulse rounded-full bg-green-400"></div>
								<span class="text-sm font-medium text-white">Live: 47 members working out</span>
							</div>
						</div>
					</div>

					<!-- Floating Community Elements -->
					<div
						class="absolute -top-4 -right-4 flex h-16 w-16 items-center justify-center rounded-full bg-black"
					>
						<svg class="h-8 w-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"
							/>
						</svg>
					</div>
				</div>
			</div>

			<!-- Community Benefits -->
			<div
				class="transform transition-all delay-600 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="space-y-8">
					<!-- Support Network -->
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
										d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
									/>
								</svg>
							</div>
						</div>
						<div class="flex-1">
							<h3 class="mb-3 text-2xl font-bold text-white">Support Network</h3>
							<p class="text-lg leading-relaxed text-gray-300">
								Find your tribe of like-minded individuals who celebrate your wins, support your
								challenges, and inspire you to reach new heights.
							</p>
						</div>
					</div>

					<!-- Group Activities -->
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
										d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"
									/>
								</svg>
							</div>
						</div>
						<div class="flex-1">
							<h3 class="mb-3 text-2xl font-bold text-white">Group Events</h3>
							<p class="text-lg leading-relaxed text-gray-300">
								Join monthly challenges, social events, and community workouts that bring members
								together beyond the gym floor.
							</p>
						</div>
					</div>

					<!-- Accountability Partners -->
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
										d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"
									/>
								</svg>
							</div>
						</div>
						<div class="flex-1">
							<h3 class="mb-3 text-2xl font-bold text-white">Accountability Partners</h3>
							<p class="text-lg leading-relaxed text-gray-300">
								Connect with workout buddies who keep you motivated, consistent, and committed to
								your fitness journey.
							</p>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Community Features Grid -->
		<div
			class="grid transform grid-cols-1 gap-8 transition-all delay-800 duration-1000 md:grid-cols-3 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<!-- Member App -->
			<div
				class="rounded-3xl border border-white/10 bg-white/5 p-8 text-center transition-colors duration-300 hover:bg-white/10"
			>
				<div class="mx-auto mb-6 flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
					<svg class="h-8 w-8 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M12 18h.01M8 21h8a2 2 0 002-2V5a2 2 0 00-2-2H8a2 2 0 00-2 2v14a2 2 0 002 2z"
						/>
					</svg>
				</div>
				<h4 class="mb-3 text-xl font-bold text-white">Member App</h4>
				<p class="text-gray-300">
					Connect with fellow members, share progress, and join community challenges through our
					mobile app.
				</p>
			</div>

			<!-- Social Events -->
			<div
				class="rounded-3xl border border-white/10 bg-white/5 p-8 text-center transition-colors duration-300 hover:bg-white/10"
			>
				<div class="mx-auto mb-6 flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
					<svg class="h-8 w-8 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
						/>
					</svg>
				</div>
				<h4 class="mb-3 text-xl font-bold text-white">Social Events</h4>
				<p class="text-gray-300">
					Monthly member meetups, fitness challenges, and celebration events that build lasting
					friendships.
				</p>
			</div>

			<!-- Expert Support -->
			<div
				class="rounded-3xl border border-white/10 bg-white/5 p-8 text-center transition-colors duration-300 hover:bg-white/10"
			>
				<div class="mx-auto mb-6 flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
					<svg class="h-8 w-8 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"
						/>
					</svg>
				</div>
				<h4 class="mb-3 text-xl font-bold text-white">Expert Support</h4>
				<p class="text-gray-300">
					Trainers and nutritionists who are part of the community, providing ongoing guidance and
					support.
				</p>
			</div>
		</div>

		<!-- Join Community CTA -->
		<div
			class="mt-16 transform text-center transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-6 text-3xl font-bold text-white">Ready to join our community?</h3>
			<div class="inline-flex flex-col gap-4 sm:flex-row">
				<button
					class="rounded-2xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
				>
					Start Your Journey Today
				</button>
				<button
					class="rounded-2xl border-2 border-white px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
				>
					Visit Our Community
				</button>
			</div>
		</div>
	</div>
</section>

<style>
	@keyframes pulse {
		0%,
		100% {
			opacity: 1;
		}
		50% {
			opacity: 0.5;
		}
	}

	.animate-pulse {
		animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
	}
</style>
