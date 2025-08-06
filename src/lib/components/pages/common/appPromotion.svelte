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
					<span class="text-sm font-medium text-white/70">📱 Power House App</span>
				</div>

				<h2 class="mb-6 text-5xl font-black text-white md:text-6xl lg:text-7xl">
					GET THE <span
						class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
						>POWER HOUSE APP</span
					>
				</h2>

				<p class="mx-auto max-w-4xl text-xl leading-relaxed text-gray-300 md:text-2xl">
					Maximize your membership and stay connected to your fitness journey with the Power House
					Training app.
					<span class="font-semibold text-white">Your gym experience, elevated.</span>
				</p>
			</div>
		</div>

		<!-- Main Content -->
		<div class="grid grid-cols-1 items-center gap-16 lg:grid-cols-2">
			<!-- App Features -->
			<div
				class="transform space-y-8 transition-all delay-400 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<!-- Book Classes -->
				<div class="flex items-start space-x-6">
					<div class="flex-shrink-0">
						<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
							<svg class="h-8 w-8 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
								/>
							</svg>
						</div>
					</div>
					<div class="flex-1">
						<h3 class="mb-3 text-2xl font-bold text-white">Book Classes</h3>
						<p class="text-lg leading-relaxed text-gray-300">
							Browse and book classes, view schedules, and manage your reservations all from your
							phone.
						</p>
					</div>
				</div>

				<!-- Track Progress -->
				<div class="flex items-start space-x-6">
					<div class="flex-shrink-0">
						<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
							<svg class="h-8 w-8 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"
								/>
							</svg>
						</div>
					</div>
					<div class="flex-1">
						<h3 class="mb-3 text-2xl font-bold text-white">Track Progress</h3>
						<p class="text-lg leading-relaxed text-gray-300">
							Monitor your fitness journey with detailed analytics, workout history, and achievement
							tracking.
						</p>
					</div>
				</div>

				<!-- Community Features -->
				<div class="flex items-start space-x-6">
					<div class="flex-shrink-0">
						<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-black">
							<svg class="h-8 w-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
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
						<h3 class="mb-3 text-2xl font-bold text-black">Connect & Share</h3>
						<p class="text-lg leading-relaxed text-gray-600">
							Join community challenges, share achievements, and connect with fellow members.
						</p>
					</div>
				</div>

				<!-- Nutrition Plans -->
				<div class="flex items-start space-x-6">
					<div class="flex-shrink-0">
						<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-black">
							<svg class="h-8 w-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
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
						<h3 class="mb-3 text-2xl font-bold text-black">Nutrition Plans</h3>
						<p class="text-lg leading-relaxed text-gray-600">
							Access personalized meal plans and recipes curated by our expert nutritionists.
						</p>
					</div>
				</div>
			</div>

			<!-- Phone Mockup -->
			<div
				class="relative transform transition-all delay-600 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="relative mx-auto max-w-sm">
					<!-- Phone Frame -->
					<div class="relative">
						<div class="h-[640px] w-80 rounded-[3rem] bg-black p-4 shadow-2xl">
							<div class="relative h-full w-full overflow-hidden rounded-[2.5rem] bg-gray-900">
								<!-- Status Bar -->
								<div class="flex items-center justify-between px-6 py-3 text-sm text-white">
									<span class="font-semibold">9:41</span>
									<div class="flex items-center space-x-1">
										<div class="h-2 w-4 rounded-sm border border-white">
											<div class="m-px h-1 w-3 rounded-sm bg-white"></div>
										</div>
									</div>
								</div>

								<!-- App Content -->
								<div class="h-full px-6 pb-6">
									<!-- Header -->
									<div class="mb-6">
										<h4 class="mb-2 text-2xl font-bold text-white">Good Morning, Sarah!</h4>
										<p class="text-gray-400">Ready for today's workout?</p>
									</div>

									<!-- Quick Stats -->
									<div class="mb-6 grid grid-cols-2 gap-4">
										<div class="rounded-2xl bg-white/10 p-4">
											<div class="text-2xl font-bold text-white">12</div>
											<div class="text-sm text-gray-400">Classes This Month</div>
										</div>
										<div class="rounded-2xl bg-white/10 p-4">
											<div class="text-2xl font-bold text-white">5</div>
											<div class="text-sm text-gray-400">Streak Days</div>
										</div>
									</div>

									<!-- Today's Class -->
									<div class="mb-6 rounded-2xl bg-white p-4">
										<div class="mb-3 flex items-center justify-between">
											<h5 class="font-bold text-black">Today's Class</h5>
											<span class="text-sm text-gray-600">6:00 PM</span>
										</div>
										<div class="mb-2 font-semibold text-black">Strength Training</div>
										<div class="mb-3 text-sm text-gray-600">Studio A • Coach Mike</div>
										<button class="w-full rounded-lg bg-black py-2 font-semibold text-white">
											Join Class
										</button>
									</div>

									<!-- Weekly Progress -->
									<div class="rounded-2xl bg-white/10 p-4">
										<h5 class="mb-3 font-semibold text-white">Weekly Progress</h5>
										<div class="flex h-16 items-end space-x-2">
											{#each [60, 80, 45, 90, 70, 30, 85] as height}
												<div class="flex-1 rounded-t bg-white/30" style="height: {height}%"></div>
											{/each}
										</div>
									</div>
								</div>
							</div>
						</div>
					</div>

					<!-- Floating Elements -->
					<div
						class="absolute -top-8 -left-8 flex h-16 w-16 animate-bounce items-center justify-center rounded-full bg-black"
					>
						<svg class="h-8 w-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M12 18h.01M8 21h8a2 2 0 002-2V5a2 2 0 00-2-2H8a2 2 0 00-2 2v14a2 2 0 002 2z"
							/>
						</svg>
					</div>

					<div
						class="absolute -right-8 -bottom-8 flex h-20 w-20 items-center justify-center rounded-full bg-gradient-to-br from-gray-200 to-gray-400"
					>
						<svg class="h-10 w-10 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
							/>
						</svg>
					</div>
				</div>
			</div>
		</div>

		<!-- App Features Grid -->
		<div
			class="mt-20 grid transform grid-cols-1 gap-6 transition-all delay-800 duration-1000 md:grid-cols-4 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<!-- Home Workouts -->
			<div
				class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center transition-colors duration-300 hover:bg-white/10"
			>
				<div class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-xl bg-white">
					<svg class="h-6 w-6 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"
						/>
					</svg>
				</div>
				<h5 class="mb-2 font-bold text-white">Home Workouts</h5>
				<p class="text-sm text-gray-300">Train anywhere with guided video workouts</p>
			</div>

			<!-- Meal Planning -->
			<div
				class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center transition-colors duration-300 hover:bg-white/10"
			>
				<div class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-xl bg-white">
					<svg class="h-6 w-6 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 100 4m0-4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 100 4m0-4v2m0-6V4"
						/>
					</svg>
				</div>
				<h5 class="mb-2 font-bold text-white">Meal Planning</h5>
				<p class="text-sm text-gray-300">Personalized nutrition plans and recipes</p>
			</div>

			<!-- Progress Tracking -->
			<div
				class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center transition-colors duration-300 hover:bg-white/10"
			>
				<div class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-xl bg-white">
					<svg class="h-6 w-6 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M16 8v8m-4-5v5m-4-2v2m-2 4h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"
						/>
					</svg>
				</div>
				<h5 class="mb-2 font-bold text-white">Progress Reports</h5>
				<p class="text-sm text-gray-300">Detailed analytics and achievement tracking</p>
			</div>

			<!-- Social Features -->
			<div
				class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center transition-colors duration-300 hover:bg-white/10"
			>
				<div class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-xl bg-white">
					<svg class="h-6 w-6 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197m13.5-9a2.5 2.5 0 11-5 0 2.5 2.5 0 015 0z"
						/>
					</svg>
				</div>
				<h5 class="mb-2 font-bold text-white">Social Hub</h5>
				<p class="text-sm text-gray-300">Connect with friends and join challenges</p>
			</div>
		</div>

		<!-- Download Section -->
		<div
			class="mt-16 transform text-center transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-8 text-3xl font-bold text-white">Download the Power House App</h3>
			<div class="flex flex-col items-center justify-center gap-4 sm:flex-row">
				<!-- App Store Button -->
				<button
					class="flex items-center space-x-3 rounded-2xl bg-white px-6 py-3 text-black transition-colors duration-300 hover:bg-gray-200"
				>
					<svg class="h-8 w-8" viewBox="0 0 24 24" fill="currentColor">
						<path
							d="M18.71 19.5c-.83 1.24-1.71 2.45-3.05 2.47-1.34.03-1.77-.79-3.29-.79-1.53 0-2 .77-3.27.82-1.31.05-2.3-1.32-3.14-2.53C4.25 17 2.94 12.45 4.7 9.39c.87-1.52 2.43-2.48 4.12-2.51 1.28-.02 2.5.87 3.29.87.78 0 2.26-1.07 3.81-.91.65.03 2.47.26 3.64 1.98-.09.06-2.17 1.28-2.15 3.81.03 3.02 2.65 4.03 2.68 4.04-.03.07-.42 1.44-1.38 2.83M13 3.5c.73-.83 1.94-1.46 2.94-1.5.13 1.17-.34 2.35-1.04 3.19-.69.85-1.83 1.51-2.95 1.42-.15-1.15.41-2.35 1.05-3.11z"
						/>
					</svg>
					<div class="text-left">
						<div class="text-xs">Download on the</div>
						<div class="text-lg font-semibold">App Store</div>
					</div>
				</button>

				<!-- Google Play Button -->
				<button
					class="flex items-center space-x-3 rounded-2xl bg-white px-6 py-3 text-black transition-colors duration-300 hover:bg-gray-200"
				>
					<svg class="h-8 w-8" viewBox="0 0 24 24" fill="currentColor">
						<path
							d="M3,20.5V3.5C3,2.91 3.34,2.39 3.84,2.15L13.69,12L3.84,21.85C3.34,21.6 3,21.09 3,20.5M16.81,15.12L6.05,21.34L14.54,12.85L16.81,15.12M20.16,10.81C20.5,11.08 20.75,11.5 20.75,12C20.75,12.5 20.53,12.9 20.18,13.18L17.89,14.5L15.39,12L17.89,9.5L20.16,10.81M6.05,2.66L16.81,8.88L14.54,11.15L6.05,2.66Z"
						/>
					</svg>
					<div class="text-left">
						<div class="text-xs">Get it on</div>
						<div class="text-lg font-semibold">Google Play</div>
					</div>
				</button>
			</div>
		</div>
	</div>
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
</style>
