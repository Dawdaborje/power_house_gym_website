<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	interface Addon {
		id: string;
		name: string;
		description: string;
		price: number;
		unit: string;
		icon: string;
		features: string[];
		popular?: boolean;
		availableFor: string[];
		category: 'training' | 'wellness' | 'nutrition' | 'equipment';
	}

	const addons: Addon[] = [
		{
			id: 'personal-training',
			name: 'Personal Training',
			description: 'One-on-one sessions with certified trainers',
			price: 75,
			unit: 'per session',
			icon: '🏋️‍♂️',
			popular: true,
			category: 'training',
			availableFor: ['Basic', 'Premium'],
			features: [
				'Customized workout plans',
				'Form correction and technique',
				'Goal-specific programming',
				'Progress tracking',
				'Nutritional guidance',
				'Flexible scheduling'
			]
		},
		{
			id: 'group-training',
			name: 'Small Group Training',
			description: 'Semi-private sessions with 2-4 people',
			price: 35,
			unit: 'per session',
			icon: '👥',
			category: 'training',
			availableFor: ['Basic', 'Premium', 'Elite'],
			features: [
				'2-4 person groups',
				'Shared training costs',
				'Social motivation',
				'Customized group workouts',
				'Professional coaching',
				'Team building elements'
			]
		},
		{
			id: 'nutrition-coaching',
			name: 'Nutrition Coaching',
			description: 'Personalized meal plans and nutrition guidance',
			price: 150,
			unit: 'per month',
			icon: '🥗',
			category: 'nutrition',
			availableFor: ['Basic', 'Premium'],
			features: [
				'Custom meal planning',
				'Macronutrient tracking',
				'Grocery shopping lists',
				'Recipe recommendations',
				'Weekly check-ins',
				'Supplement guidance'
			]
		},
		{
			id: 'massage-therapy',
			name: 'Massage Therapy',
			description: 'Professional therapeutic massage sessions',
			price: 120,
			unit: 'per session',
			icon: '💆‍♀️',
			category: 'wellness',
			availableFor: ['Basic', 'Premium'],
			features: [
				'Licensed massage therapists',
				'Deep tissue massage',
				'Sports massage',
				'Recovery focused',
				'Injury prevention',
				'Stress relief'
			]
		},
		{
			id: 'body-composition',
			name: 'Body Composition Analysis',
			description: 'Detailed body composition and progress tracking',
			price: 50,
			unit: 'per scan',
			icon: '📊',
			category: 'wellness',
			availableFor: ['Basic', 'Premium'],
			features: [
				'DEXA scan technology',
				'Muscle mass analysis',
				'Body fat percentage',
				'Bone density measurement',
				'Progress tracking',
				'Professional interpretation'
			]
		},
		{
			id: 'equipment-rental',
			name: 'Equipment Rental',
			description: 'Take gym equipment home for your workouts',
			price: 25,
			unit: 'per week',
			icon: '🏠',
			category: 'equipment',
			availableFor: ['Premium', 'Elite'],
			features: [
				'Dumbbells and kettlebells',
				'Resistance bands',
				'Yoga mats and blocks',
				'Foam rollers',
				'Workout accessories',
				'Delivery and pickup'
			]
		},
		{
			id: 'guest-passes',
			name: 'Additional Guest Passes',
			description: 'Bring friends and family to work out with you',
			price: 15,
			unit: 'per pass',
			icon: '🎫',
			category: 'training',
			availableFor: ['Basic', 'Premium'],
			features: [
				'Single-day gym access',
				'All equipment included',
				'Group class access',
				'Locker room privileges',
				'Valid for 30 days',
				'No commitment required'
			]
		},
		{
			id: 'virtual-training',
			name: 'Virtual Personal Training',
			description: 'Online one-on-one training sessions',
			price: 50,
			unit: 'per session',
			icon: '💻',
			category: 'training',
			availableFor: ['Basic', 'Premium', 'Elite'],
			features: [
				'Live video sessions',
				'Flexible scheduling',
				'Home workout plans',
				'Equipment alternatives',
				'Progress monitoring',
				'Record sessions for review'
			]
		}
	];

	const categories = {
		training: { name: 'Training', color: 'bg-red-500' },
		wellness: { name: 'Wellness', color: 'bg-green-500' },
		nutrition: { name: 'Nutrition', color: 'bg-yellow-500' },
		equipment: { name: 'Equipment', color: 'bg-blue-500' }
	};

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});
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
				<span class="text-sm font-medium text-white/70">🔧 Enhance Your Experience</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				ADD-ONS &
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					SERVICES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Enhance your membership with our premium add-on services. From personal training to massage
				therapy, we have everything you need to maximize your fitness results.
			</p>
		</div>

		<!-- Add-ons Grid -->
		<div
			class="grid transform grid-cols-1 gap-8 transition-all delay-400 duration-1000 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each addons as addon, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10 hover:scale-105"
					style="transition-delay: {index * 100}ms"
				>
					<!-- Popular Badge -->
					{#if addon.popular}
						<div
							class="absolute -top-3 -right-3 rounded-full bg-green-500 px-3 py-1 text-xs font-bold text-white"
						>
							Popular
						</div>
					{/if}

					<div class="p-6">
						<!-- Header -->
						<div class="mb-6 text-center">
							<div class="mb-3 text-4xl">{addon.icon}</div>
							<h3 class="mb-2 text-lg font-bold text-white">{addon.name}</h3>
							<div
								class="mb-2 inline-block rounded-full px-3 py-1 text-xs font-medium text-white {categories[
									addon.category
								].color}"
							>
								{categories[addon.category].name}
							</div>
							<p class="text-sm text-gray-400">{addon.description}</p>
						</div>

						<!-- Pricing -->
						<div class="mb-6 text-center">
							<div class="text-3xl font-black text-white">${addon.price}</div>
							<div class="text-sm text-gray-400">{addon.unit}</div>
						</div>

						<!-- Available For -->
						<div class="mb-6">
							<div class="mb-2 text-sm font-semibold text-white">Available for:</div>
							<div class="flex flex-wrap gap-1">
								{#each addon.availableFor as plan}
									<span
										class="rounded-full bg-white/10 px-2 py-1 text-xs font-medium text-white"
									>
										{plan}
									</span>
								{/each}
							</div>
						</div>

						<!-- Features -->
						<div class="mb-6">
							<div class="mb-3 text-sm font-semibold text-white">Includes:</div>
							<ul class="space-y-2">
								{#each addon.features.slice(0, 4) as feature}
									<li class="flex items-start space-x-2">
										<svg
											class="mt-0.5 h-4 w-4 flex-shrink-0 text-green-400"
											fill="currentColor"
											viewBox="0 0 20 20"
										>
											<path
												fill-rule="evenodd"
												d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
												clip-rule="evenodd"
											/>
										</svg>
										<span class="text-sm text-gray-300">{feature}</span>
									</li>
								{/each}
								{#if addon.features.length > 4}
									<li class="text-sm text-gray-400">
										+ {addon.features.length - 4} more features
									</li>
								{/if}
							</ul>
						</div>

						<!-- CTA Button -->
						<button
							class="w-full rounded-xl bg-white px-4 py-3 text-sm font-bold text-black transition-all duration-300 hover:bg-gray-200"
						>
							Add to Plan
						</button>
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

		<!-- Package Deals -->
		<div
			class="mt-20 transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-8 text-center text-3xl font-bold text-white">Package Deals</h3>
			<div class="grid grid-cols-1 gap-8 lg:grid-cols-2">
				<!-- Wellness Package -->
				<div
					class="rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
				>
					<div class="mb-4 text-5xl">🧘‍♀️</div>
					<h4 class="mb-3 text-2xl font-bold text-white">Wellness Package</h4>
					<p class="mb-6 text-gray-300">
						Complete wellness experience with massage therapy and body composition analysis
					</p>
					<div class="mb-6">
						<span class="mr-2 text-lg text-gray-400 line-through">$340/month</span>
						<span class="text-3xl font-black text-white">$275/month</span>
						<div class="text-sm text-green-400">Save $65/month</div>
					</div>
					<ul class="mb-6 space-y-2 text-left">
						<li class="flex items-center space-x-2">
							<svg class="h-4 w-4 text-green-400" fill="currentColor" viewBox="0 0 20 20">
								<path
									fill-rule="evenodd"
									d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
									clip-rule="evenodd"
								/>
							</svg>
							<span class="text-gray-300">2 massage sessions per month</span>
						</li>
						<li class="flex items-center space-x-2">
							<svg class="h-4 w-4 text-green-400" fill="currentColor" viewBox="0 0 20 20">
								<path
									fill-rule="evenodd"
									d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
									clip-rule="evenodd"
								/>
							</svg>
							<span class="text-gray-300">Monthly body composition analysis</span>
						</li>
						<li class="flex items-center space-x-2">
							<svg class="h-4 w-4 text-green-400" fill="currentColor" viewBox="0 0 20 20">
								<path
									fill-rule="evenodd"
									d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
									clip-rule="evenodd"
								/>
							</svg>
							<span class="text-gray-300">Nutrition consultation</span>
						</li>
					</ul>
					<button
						class="w-full rounded-xl bg-white px-6 py-3 font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Choose Wellness Package
					</button>
				</div>

				<!-- Training Package -->
				<div
					class="rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
				>
					<div class="mb-4 text-5xl">💪</div>
					<h4 class="mb-3 text-2xl font-bold text-white">Training Package</h4>
					<p class="mb-6 text-gray-300">
						Comprehensive training solution with personal and group sessions
					</p>
					<div class="mb-6">
						<span class="mr-2 text-lg text-gray-400 line-through">$440/month</span>
						<span class="text-3xl font-black text-white">$350/month</span>
						<div class="text-sm text-green-400">Save $90/month</div>
					</div>
					<ul class="mb-6 space-y-2 text-left">
						<li class="flex items-center space-x-2">
							<svg class="h-4 w-4 text-green-400" fill="currentColor" viewBox="0 0 20 20">
								<path
									fill-rule="evenodd"
									d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
									clip-rule="evenodd"
								/>
							</svg>
							<span class="text-gray-300">4 personal training sessions</span>
						</li>
						<li class="flex items-center space-x-2">
							<svg class="h-4 w-4 text-green-400" fill="currentColor" viewBox="0 0 20 20">
								<path
									fill-rule="evenodd"
									d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
									clip-rule="evenodd"
								/>
							</svg>
							<span class="text-gray-300">Unlimited small group training</span>
						</li>
						<li class="flex items-center space-x-2">
							<svg class="h-4 w-4 text-green-400" fill="currentColor" viewBox="0 0 20 20">
								<path
									fill-rule="evenodd"
									d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
									clip-rule="evenodd"
								/>
							</svg>
							<span class="text-gray-300">Custom workout programming</span>
						</li>
					</ul>
					<button
						class="w-full rounded-xl bg-white px-6 py-3 font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Choose Training Package
					</button>
				</div>
			</div>
		</div>

		<!-- Custom Solutions -->
		<div
			class="mt-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-3xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-4 text-2xl font-bold text-white">Need Something Custom?</h3>
				<p class="mb-6 text-gray-300">
					We offer custom packages and corporate solutions tailored to your specific needs. Contact
					our team to create the perfect plan for you.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Contact Sales Team
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						View Corporate Plans
					</button>
				</div>
			</div>
		</div>
	</div>
</section>