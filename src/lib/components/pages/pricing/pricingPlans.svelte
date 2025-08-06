<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let billingPeriod: 'monthly' | 'yearly' = 'monthly';

	interface MembershipPlan {
		id: string;
		name: string;
		tagline: string;
		monthlyPrice: number;
		yearlyPrice: number;
		originalPrice?: number;
		popular?: boolean;
		features: string[];
		notIncluded?: string[];
		ctaText: string;
		description: string;
		icon: string;
		color: string;
		savings?: string;
	}

	const plans: MembershipPlan[] = [
		{
			id: 'basic',
			name: 'Basic',
			tagline: 'Perfect for beginners',
			monthlyPrice: 29,
			yearlyPrice: 290,
			originalPrice: 348,
			description: 'Essential access to get you started on your fitness journey',
			icon: '🌟',
			color: 'border-gray-500',
			features: [
				'Gym access during off-peak hours (6am-2pm weekdays)',
				'Basic cardio and weight equipment',
				'Locker room access',
				'Free gym orientation',
				'Mobile app access',
				'Community forum access'
			],
			notIncluded: [
				'Group classes',
				'Personal training',
				'Peak hour access',
				'Guest passes'
			],
			ctaText: 'Start Basic Plan',
			savings: 'Save $58/year'
		},
		{
			id: 'premium',
			name: 'Premium',
			tagline: 'Most popular choice',
			monthlyPrice: 59,
			yearlyPrice: 590,
			originalPrice: 708,
			popular: true,
			description: 'Complete fitness experience with unlimited access and group classes',
			icon: '🔥',
			color: 'border-white',
			features: [
				'24/7 unlimited gym access',
				'All cardio and weight equipment',
				'Unlimited group fitness classes',
				'Locker room with premium amenities',
				'Nutrition tracking and meal plans',
				'Community challenges and events',
				'Mobile app with workout tracking',
				'2 guest passes per month',
				'Towel service',
				'Free parking'
			],
			notIncluded: [
				'Personal training sessions',
				'Massage therapy',
				'Sauna access'
			],
			ctaText: 'Choose Premium',
			savings: 'Save $118/year'
		},
		{
			id: 'elite',
			name: 'Elite',
			tagline: 'Ultimate fitness experience',
			monthlyPrice: 99,
			yearlyPrice: 990,
			originalPrice: 1188,
			description: 'Premium everything plus personal training and exclusive perks',
			icon: '👑',
			color: 'border-yellow-400',
			features: [
				'Everything in Premium plan',
				'4 personal training sessions per month',
				'Unlimited sauna and steam room access',
				'Monthly massage therapy session',
				'Priority booking for classes',
				'Exclusive member events',
				'Nutrition consultation with dietitian',
				'Body composition analysis',
				'Recovery zone access',
				'Unlimited guest passes',
				'Priority customer support',
				'Exclusive Elite merchandise'
			],
			ctaText: 'Go Elite',
			savings: 'Save $198/year'
		}
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function getCurrentPrice(plan: MembershipPlan) {
		return billingPeriod === 'monthly' ? plan.monthlyPrice : plan.yearlyPrice;
	}

	function getOriginalPrice(plan: MembershipPlan) {
		return billingPeriod === 'monthly' ? plan.monthlyPrice : plan.originalPrice;
	}

	function formatPrice(price: number) {
		if (billingPeriod === 'yearly') {
			return `$${price}`;
		}
		return `$${price}`;
	}

	function getPeriodText() {
		return billingPeriod === 'monthly' ? '/month' : '/year';
	}
</script>

<section class="bg-black py-24">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<!-- Section Header -->
		<div
			class="mb-20 transform text-center transition-all delay-200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mb-6 inline-flex items-center rounded-full border border-white/10 bg-white/5 px-6 py-2"
			>
				<span class="text-sm font-medium text-white/70">💰 Choose Your Plan</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				MEMBERSHIP
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					PLANS
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Choose the perfect plan for your fitness goals. All plans include our core facilities and
				community support. Upgrade or downgrade anytime.
			</p>

			<!-- Billing Toggle -->
			<div class="mt-8 flex items-center justify-center">
				<div class="flex rounded-2xl border border-white/10 bg-white/5 p-2">
					<button
						on:click={() => (billingPeriod = 'monthly')}
						class="rounded-xl px-6 py-3 text-sm font-semibold transition-all duration-300 {billingPeriod ===
						'monthly'
							? 'bg-white text-black shadow-lg'
							: 'text-white hover:bg-white/10'}"
					>
						Monthly
					</button>
					<button
						on:click={() => (billingPeriod = 'yearly')}
						class="relative rounded-xl px-6 py-3 text-sm font-semibold transition-all duration-300 {billingPeriod ===
						'yearly'
							? 'bg-white text-black shadow-lg'
							: 'text-white hover:bg-white/10'}"
					>
						Yearly
						<span
							class="absolute -top-2 -right-2 rounded-full bg-green-500 px-2 py-0.5 text-xs font-bold text-white"
						>
							Save 20%
						</span>
					</button>
				</div>
			</div>
		</div>

		<!-- Pricing Plans Grid -->
		<div
			class="grid transform grid-cols-1 gap-8 transition-all delay-400 duration-1000 lg:grid-cols-3 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each plans as plan, index}
				<div
					class="group relative overflow-hidden rounded-3xl border-2 bg-white/5 backdrop-blur-md transition-all duration-500 hover:bg-white/10 hover:scale-105 {plan.color} {plan.popular
						? 'scale-105 shadow-2xl shadow-white/10'
						: ''}"
					style="transition-delay: {index * 150}ms"
				>
					<!-- Popular Badge -->
					{#if plan.popular}
						<div
							class="absolute -top-4 left-1/2 -translate-x-1/2 transform rounded-full bg-white px-6 py-2 text-sm font-bold text-black"
						>
							Most Popular
						</div>
					{/if}

					<div class="p-8">
						<!-- Plan Header -->
						<div class="mb-8 text-center">
							<div class="mb-4 text-5xl">{plan.icon}</div>
							<h3 class="mb-2 text-2xl font-bold text-white">{plan.name}</h3>
							<p class="text-gray-400">{plan.tagline}</p>
						</div>

						<!-- Pricing -->
						<div class="mb-8 text-center">
							<div class="mb-2 flex items-baseline justify-center">
								{#if billingPeriod === 'yearly' && plan.originalPrice}
									<span class="mr-2 text-lg text-gray-400 line-through">
										{formatPrice(plan.originalPrice)}
									</span>
								{/if}
								<span class="text-5xl font-black text-white">
									{formatPrice(getCurrentPrice(plan))}
								</span>
								<span class="ml-1 text-lg text-gray-400">{getPeriodText()}</span>
							</div>
							{#if billingPeriod === 'yearly' && plan.savings}
								<div class="text-sm font-medium text-green-400">{plan.savings}</div>
							{/if}
						</div>

						<!-- Description -->
						<p class="mb-8 text-center leading-relaxed text-gray-300">{plan.description}</p>

						<!-- Features List -->
						<div class="mb-8">
							<h4 class="mb-4 text-lg font-semibold text-white">What's included:</h4>
							<ul class="space-y-3">
								{#each plan.features as feature}
									<li class="flex items-start space-x-3">
										<svg
											class="mt-0.5 h-5 w-5 flex-shrink-0 text-green-400"
											fill="currentColor"
											viewBox="0 0 20 20"
										>
											<path
												fill-rule="evenodd"
												d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
												clip-rule="evenodd"
											/>
										</svg>
										<span class="text-gray-300">{feature}</span>
									</li>
								{/each}
							</ul>
						</div>

						<!-- Not Included (if any) -->
						{#if plan.notIncluded && plan.notIncluded.length > 0}
							<div class="mb-8">
								<h4 class="mb-4 text-lg font-semibold text-white">Not included:</h4>
								<ul class="space-y-3">
									{#each plan.notIncluded as feature}
										<li class="flex items-start space-x-3">
											<svg
												class="mt-0.5 h-5 w-5 flex-shrink-0 text-gray-500"
												fill="currentColor"
												viewBox="0 0 20 20"
											>
												<path
													fill-rule="evenodd"
													d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
													clip-rule="evenodd"
												/>
											</svg>
											<span class="text-gray-500">{feature}</span>
										</li>
									{/each}
								</ul>
							</div>
						{/if}

						<!-- CTA Button -->
						<button
							class="w-full rounded-xl px-6 py-4 text-lg font-bold transition-all duration-300 {plan.popular
								? 'bg-white text-black hover:bg-gray-200'
								: 'border-2 border-white bg-transparent text-white hover:bg-white hover:text-black'}"
						>
							{plan.ctaText}
						</button>

						<!-- Money Back Guarantee -->
						<div class="mt-4 text-center">
							<span class="text-sm text-gray-400">30-day money-back guarantee</span>
						</div>
					</div>

					<!-- Hover Overlay -->
					<div
						class="absolute inset-0 opacity-0 transition-opacity duration-300 group-hover:opacity-100"
					>
						<div
							class="absolute inset-0 bg-gradient-to-t from-white/5 via-transparent to-transparent"
						></div>
					</div>
				</div>
			{/each}
		</div>

		<!-- Additional Info -->
		<div
			class="mt-20 transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-6 text-2xl font-bold text-white">All Plans Include</h3>
				<div class="grid grid-cols-1 gap-6 md:grid-cols-4">
					<div class="text-center">
						<div class="mb-2 text-3xl">🎯</div>
						<div class="font-semibold text-white">Goal Setting</div>
						<div class="text-sm text-gray-400">Personal fitness assessment</div>
					</div>
					<div class="text-center">
						<div class="mb-2 text-3xl">📱</div>
						<div class="font-semibold text-white">Mobile App</div>
						<div class="text-sm text-gray-400">Track progress & book classes</div>
					</div>
					<div class="text-center">
						<div class="mb-2 text-3xl">🏆</div>
						<div class="font-semibold text-white">Community</div>
						<div class="text-sm text-gray-400">Challenges & events</div>
					</div>
					<div class="text-center">
						<div class="mb-2 text-3xl">🔒</div>
						<div class="font-semibold text-white">No Lock-in</div>
						<div class="text-sm text-gray-400">Cancel anytime</div>
					</div>
				</div>

				<div class="mt-8 border-t border-white/10 pt-6">
					<p class="text-gray-300">
						Need help choosing? Our team is here to help you find the perfect plan.
						<a href="#" class="font-semibold text-white hover:text-gray-300">Contact us</a>
						for a free consultation.
					</p>
				</div>
			</div>
		</div>
	</div>
</section>