<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	interface Feature {
		category: string;
		items: {
			name: string;
			basic: boolean | string;
			premium: boolean | string;
			elite: boolean | string;
			description?: string;
		}[];
	}

	const features: Feature[] = [
		{
			category: 'Gym Access',
			items: [
				{
					name: 'Gym Hours',
					basic: '6am-2pm weekdays',
					premium: '24/7 access',
					elite: '24/7 access',
					description: 'When you can access the gym'
				},
				{
					name: 'Equipment Access',
					basic: 'Basic cardio & weights',
					premium: 'All equipment',
					elite: 'All equipment + priority',
					description: 'Which equipment you can use'
				},
				{
					name: 'Locker Room',
					basic: true,
					premium: true,
					elite: true,
					description: 'Standard locker room access'
				},
				{
					name: 'Free Parking',
					basic: false,
					premium: true,
					elite: true,
					description: 'Complimentary parking space'
				}
			]
		},
		{
			category: 'Classes & Training',
			items: [
				{
					name: 'Group Fitness Classes',
					basic: false,
					premium: 'Unlimited',
					elite: 'Unlimited + priority',
					description: 'Access to group fitness classes'
				},
				{
					name: 'Personal Training',
					basic: false,
					premium: 'Add-on available',
					elite: '4 sessions/month',
					description: 'One-on-one training sessions'
				},
				{
					name: 'Nutrition Consultation',
					basic: false,
					premium: 'Basic meal plans',
					elite: 'Full consultation',
					description: 'Personalized nutrition guidance'
				},
				{
					name: 'Body Composition Analysis',
					basic: false,
					premium: false,
					elite: 'Monthly',
					description: 'Professional body analysis'
				}
			]
		},
		{
			category: 'Amenities',
			items: [
				{
					name: 'Sauna & Steam Room',
					basic: false,
					premium: false,
					elite: 'Unlimited access',
					description: 'Recovery and relaxation facilities'
				},
				{
					name: 'Towel Service',
					basic: false,
					premium: true,
					elite: true,
					description: 'Fresh towels provided'
				},
				{
					name: 'Massage Therapy',
					basic: false,
					premium: 'Add-on available',
					elite: '1 session/month',
					description: 'Professional massage therapy'
				},
				{
					name: 'Recovery Zone',
					basic: false,
					premium: false,
					elite: true,
					description: 'Specialized recovery equipment'
				}
			]
		},
		{
			category: 'Community & Perks',
			items: [
				{
					name: 'Guest Passes',
					basic: false,
					premium: '2 per month',
					elite: 'Unlimited',
					description: 'Bring friends to work out'
				},
				{
					name: 'Community Events',
					basic: true,
					premium: true,
					elite: 'VIP access',
					description: 'Member social events and challenges'
				},
				{
					name: 'Mobile App',
					basic: 'Basic features',
					premium: 'Full features',
					elite: 'Premium features',
					description: 'Workout tracking and class booking'
				},
				{
					name: 'Customer Support',
					basic: 'Standard',
					premium: 'Priority',
					elite: 'VIP support',
					description: 'Level of customer service'
				}
			]
		}
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function renderFeatureValue(value: boolean | string) {
		if (typeof value === 'boolean') {
			return value;
		}
		return value;
	}

	function getFeatureIcon(value: boolean | string) {
		if (value === false) {
			return '❌';
		}
		if (value === true) {
			return '✅';
		}
		return '📋';
	}

	function getFeatureClass(value: boolean | string) {
		if (value === false) {
			return 'text-gray-500';
		}
		if (value === true) {
			return 'text-green-400';
		}
		return 'text-white';
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
				<span class="text-sm font-medium text-white/70">🔍 Compare Plans</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				FEATURES
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					COMPARISON
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Compare all features across our membership plans to find the perfect fit for your fitness
				goals and lifestyle.
			</p>
		</div>

		<!-- Comparison Table -->
		<div
			class="transform transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<!-- Mobile View -->
			<div class="block lg:hidden">
				<div class="space-y-8">
					{#each features as category, categoryIndex}
						<div
							class="rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md"
							style="transition-delay: {categoryIndex * 100}ms"
						>
							<h3 class="mb-6 text-xl font-bold text-white">{category.category}</h3>
							<div class="space-y-4">
								{#each category.items as item}
									<div class="rounded-xl border border-white/10 bg-white/5 p-4">
										<h4 class="mb-3 font-semibold text-white">{item.name}</h4>
										<div class="grid grid-cols-3 gap-4 text-sm">
											<div class="text-center">
												<div class="mb-1 text-xs font-medium text-gray-400">Basic</div>
												<div class="{getFeatureClass(item.basic)} font-medium">
													{typeof item.basic === 'boolean'
														? item.basic
															? '✅'
															: '❌'
														: item.basic}
												</div>
											</div>
											<div class="text-center">
												<div class="mb-1 text-xs font-medium text-gray-400">Premium</div>
												<div class="{getFeatureClass(item.premium)} font-medium">
													{typeof item.premium === 'boolean'
														? item.premium
															? '✅'
															: '❌'
														: item.premium}
												</div>
											</div>
											<div class="text-center">
												<div class="mb-1 text-xs font-medium text-gray-400">Elite</div>
												<div class="{getFeatureClass(item.elite)} font-medium">
													{typeof item.elite === 'boolean'
														? item.elite
															? '✅'
															: '❌'
														: item.elite}
												</div>
											</div>
										</div>
									</div>
								{/each}
							</div>
						</div>
					{/each}
				</div>
			</div>

			<!-- Desktop View -->
			<div class="hidden lg:block">
				<div class="overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md">
					<!-- Table Header -->
					<div class="grid grid-cols-4 border-b border-white/10 bg-white/10 p-6">
						<div class="text-lg font-bold text-white">Features</div>
						<div class="text-center">
							<div class="text-lg font-bold text-white">Basic</div>
							<div class="text-sm text-gray-400">$29/month</div>
						</div>
						<div class="text-center">
							<div class="text-lg font-bold text-white">Premium</div>
							<div class="text-sm text-gray-400">$59/month</div>
							<div class="text-xs font-medium text-green-400">Most Popular</div>
						</div>
						<div class="text-center">
							<div class="text-lg font-bold text-white">Elite</div>
							<div class="text-sm text-gray-400">$99/month</div>
						</div>
					</div>

					<!-- Feature Categories -->
					{#each features as category, categoryIndex}
						<div
							class="border-b border-white/10"
							style="transition-delay: {categoryIndex * 150}ms"
						>
							<!-- Category Header -->
							<div class="bg-white/5 px-6 py-4">
								<h3 class="text-lg font-semibold text-white">{category.category}</h3>
							</div>

							<!-- Feature Rows -->
							{#each category.items as item, itemIndex}
								<div
									class="grid grid-cols-4 border-b border-white/5 p-6 transition-colors hover:bg-white/5"
									style="transition-delay: {(categoryIndex * category.items.length + itemIndex) * 50}ms"
								>
									<div class="flex flex-col">
										<span class="font-medium text-white">{item.name}</span>
										{#if item.description}
											<span class="text-sm text-gray-400">{item.description}</span>
										{/if}
									</div>

									<!-- Basic -->
									<div class="flex items-center justify-center">
										{#if typeof item.basic === 'boolean'}
											<span class="text-2xl">
												{item.basic ? '✅' : '❌'}
											</span>
										{:else}
											<span class="text-center font-medium text-white">{item.basic}</span>
										{/if}
									</div>

									<!-- Premium -->
									<div class="flex items-center justify-center">
										{#if typeof item.premium === 'boolean'}
											<span class="text-2xl">
												{item.premium ? '✅' : '❌'}
											</span>
										{:else}
											<span class="text-center font-medium text-white">{item.premium}</span>
										{/if}
									</div>

									<!-- Elite -->
									<div class="flex items-center justify-center">
										{#if typeof item.elite === 'boolean'}
											<span class="text-2xl">
												{item.elite ? '✅' : '❌'}
											</span>
										{:else}
											<span class="text-center font-medium text-white">{item.elite}</span>
										{/if}
									</div>
								</div>
							{/each}
						</div>
					{/each}

					<!-- CTA Row -->
					<div class="grid grid-cols-4 p-6">
						<div></div>
						<div class="px-4">
							<button
								class="w-full rounded-xl border-2 border-white bg-transparent py-3 text-sm font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
							>
								Choose Basic
							</button>
						</div>
						<div class="px-4">
							<button
								class="w-full rounded-xl bg-white py-3 text-sm font-bold text-black transition-all duration-300 hover:bg-gray-200"
							>
								Choose Premium
							</button>
						</div>
						<div class="px-4">
							<button
								class="w-full rounded-xl border-2 border-yellow-400 bg-transparent py-3 text-sm font-bold text-yellow-400 transition-all duration-300 hover:bg-yellow-400 hover:text-black"
							>
								Choose Elite
							</button>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Help Section -->
		<div
			class="mt-20 transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-2xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-4 text-2xl font-bold text-white">Still Have Questions?</h3>
				<p class="mb-6 text-gray-300">
					Our team is here to help you choose the perfect membership plan for your goals and budget.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Schedule Consultation
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						View FAQ
					</button>
				</div>
			</div>
		</div>
	</div>
</section>