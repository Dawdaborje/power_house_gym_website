<script lang="ts">
	import { onMount } from 'svelte';

	let sectionRef: HTMLElement;
	let isVisible = false;

	const plans = [
		{
			id: 'starter',
			name: 'Starter',
			price: 89,
			period: 'month',
			popular: false,
			description: 'Perfect for getting started on your fitness journey',
			features: [
				'Unlimited gym access',
				'Group fitness classes',
				'Basic equipment orientation',
				'Mobile app access',
				'Locker room access'
			],
			buttonText: 'Start Free Trial',
			highlight: false
		},
		{
			id: 'premium',
			name: 'Premium',
			price: 149,
			period: 'month',
			popular: true,
			description: 'Most popular choice for serious fitness enthusiasts',
			features: [
				'Everything in Starter',
				'Personal training sessions (2/month)',
				'Nutrition consultation',
				'Priority class booking',
				'Guest privileges (2/month)',
				'Recovery zone access'
			],
			buttonText: 'Start Free Trial',
			highlight: true
		},
		{
			id: 'elite',
			name: 'Elite',
			price: 249,
			period: 'month',
			popular: false,
			description: 'Ultimate experience with VIP treatment',
			features: [
				'Everything in Premium',
				'Unlimited personal training',
				'Custom meal planning',
				'VIP locker room',
				'Unlimited guest privileges',
				'24/7 concierge support',
				'Exclusive member events'
			],
			buttonText: 'Contact Us',
			highlight: false
		}
	];

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
					<span class="text-sm font-medium text-white/70">🚀 Join Power House</span>
				</div>

				<h2 class="mb-6 text-5xl font-black text-white md:text-6xl lg:text-7xl">
					START YOUR <span
						class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
						>TRANSFORMATION</span
					>
				</h2>

				<p class="mx-auto max-w-4xl text-xl leading-relaxed text-gray-300 md:text-2xl">
					Choose the membership that fits your lifestyle and goals. All plans include our
					<span class="font-semibold text-white">30-day money-back guarantee.</span>
				</p>
			</div>
		</div>

		<!-- Pricing Cards -->
		<div class="mb-16 grid grid-cols-1 gap-8 md:grid-cols-3">
			{#each plans as plan, index}
				<div
					class="relative transform transition-all duration-1000 delay-{400 +
						index * 200} {isVisible ? 'translate-y-0 opacity-100' : 'translate-y-8 opacity-0'}"
				>
					<div class="relative h-full {plan.highlight ? 'scale-105 transform' : ''}">
						<!-- Popular Badge -->
						{#if plan.popular}
							<div class="absolute -top-4 left-1/2 z-10 -translate-x-1/2 transform">
								<div class="rounded-full bg-white px-6 py-2 text-sm font-bold text-black">
									MOST POPULAR
								</div>
							</div>
						{/if}

						<!-- Card -->
						<div
							class="h-full bg-white/5 {plan.highlight
								? 'border-white/20 bg-white/10'
								: 'border-white/10'} rounded-3xl border p-8 backdrop-blur-md transition-all duration-300 hover:bg-white/10"
						>
							<!-- Plan Header -->
							<div class="mb-8 text-center">
								<h3 class="mb-2 text-2xl font-bold text-white">{plan.name}</h3>
								<p class="mb-6 text-gray-300">{plan.description}</p>

								<!-- Pricing -->
								<div class="mb-6">
									<div class="flex items-baseline justify-center">
										<span class="text-5xl font-black text-white">${plan.price}</span>
										<span class="ml-2 text-xl text-gray-300">/{plan.period}</span>
									</div>
									{#if plan.id === 'starter'}
										<p class="mt-2 text-sm text-gray-400">First month free for new members</p>
									{/if}
								</div>
							</div>

							<!-- Features -->
							<div class="mb-8 space-y-4">
								{#each plan.features as feature}
									<div class="flex items-center space-x-3">
										<div class="flex-shrink-0">
											<svg
												class="h-5 w-5 text-green-400"
												fill="none"
												stroke="currentColor"
												viewBox="0 0 24 24"
											>
												<path
													stroke-linecap="round"
													stroke-linejoin="round"
													stroke-width="2"
													d="M5 13l4 4L19 7"
												/>
											</svg>
										</div>
										<span class="text-gray-300">{feature}</span>
									</div>
								{/each}
							</div>

							<!-- CTA Button -->
							<button
								class="w-full {plan.highlight
									? 'bg-white text-black hover:bg-gray-200'
									: 'border border-white/20 bg-white/10 text-white hover:bg-white hover:text-black'} rounded-2xl py-4 text-lg font-bold transition-all duration-300"
							>
								{plan.buttonText}
							</button>
						</div>
					</div>
				</div>
			{/each}
		</div>

		<!-- Additional Benefits -->
		<div
			class="mb-16 grid transform grid-cols-1 gap-6 transition-all delay-1000 duration-1000 md:grid-cols-4 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<!-- Money Back Guarantee -->
			<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center">
				<div
					class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-xl bg-green-500"
				>
					<svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
						/>
					</svg>
				</div>
				<h5 class="mb-2 font-bold text-white">30-Day Guarantee</h5>
				<p class="text-sm text-gray-300">Full refund if not satisfied</p>
			</div>

			<!-- No Contracts -->
			<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center">
				<div class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-xl bg-blue-500">
					<svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"
						/>
					</svg>
				</div>
				<h5 class="mb-2 font-bold text-white">No Lock-in Contracts</h5>
				<p class="text-sm text-gray-300">Cancel anytime, no penalties</p>
			</div>

			<!-- Free Trial -->
			<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center">
				<div
					class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-xl bg-purple-500"
				>
					<svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
						/>
					</svg>
				</div>
				<h5 class="mb-2 font-bold text-white">7-Day Free Trial</h5>
				<p class="text-sm text-gray-300">Experience everything risk-free</p>
			</div>

			<!-- Pause Membership -->
			<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center">
				<div
					class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-xl bg-orange-500"
				>
					<svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M10 9v6m4-6v6m7-3a9 9 0 11-18 0 9 9 0 0118 0z"
						/>
					</svg>
				</div>
				<h5 class="mb-2 font-bold text-white">Flexible Pausing</h5>
				<p class="text-sm text-gray-300">Pause membership when needed</p>
			</div>
		</div>

		<!-- Special Offer -->
		<div
			class="mb-16 transform rounded-3xl border border-white/20 bg-gradient-to-r from-white/10 to-white/5 p-8 text-center transition-all delay-1200 duration-1000 md:p-12 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mx-auto max-w-3xl">
				<div class="mb-6 inline-flex items-center rounded-full bg-red-500 px-6 py-2 text-white">
					<span class="text-sm font-bold">🔥 LIMITED TIME OFFER</span>
				</div>

				<h3 class="mb-4 text-4xl font-black text-white md:text-5xl">FIRST MONTH FREE</h3>

				<p class="mb-8 text-xl text-gray-300">
					Join this month and get your first 30 days completely free. No hidden fees, no strings
					attached.
				</p>

				<div class="flex flex-col items-center justify-center gap-4 sm:flex-row">
					<button
						class="rounded-2xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Claim Free Month
					</button>
					<div class="text-sm text-white">
						<span class="font-semibold">Offer expires in:</span>
						<span class="ml-2 font-mono">7 days</span>
					</div>
				</div>
			</div>
		</div>

		<!-- FAQ Teaser -->
		<div
			class="transform text-center transition-all delay-1400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-6 text-3xl font-bold text-white">Still have questions?</h3>
			<p class="mb-8 text-xl text-gray-300">
				Our team is here to help you find the perfect membership plan.
			</p>
			<div class="flex flex-col justify-center gap-4 sm:flex-row">
				<button
					class="rounded-2xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
				>
					Book a Tour
				</button>
				<button
					class="rounded-2xl border-2 border-white px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
				>
					Contact Us
				</button>
			</div>
		</div>
	</div>
</section>

<style>
	/* Custom delay utilities for staggered animations */
	.delay-400 {
		transition-delay: 400ms;
	}
	.delay-600 {
		transition-delay: 600ms;
	}
	.delay-800 {
		transition-delay: 800ms;
	}
	.delay-1000 {
		transition-delay: 1000ms;
	}
	.delay-1200 {
		transition-delay: 1200ms;
	}
	.delay-1400 {
		transition-delay: 1400ms;
	}
</style>
