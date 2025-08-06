<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	interface CorporatePlan {
		id: string;
		name: string;
		description: string;
		minEmployees: number;
		pricePerEmployee: number;
		features: string[];
		benefits: string[];
		icon: string;
		popular?: boolean;
	}

	const corporatePlans: CorporatePlan[] = [
		{
			id: 'startup',
			name: 'Startup Plan',
			description: 'Perfect for small businesses and startups',
			minEmployees: 5,
			pricePerEmployee: 35,
			icon: '🚀',
			features: [
				'5-25 employees',
				'Basic gym access',
				'Group fitness classes',
				'Wellness workshops',
				'Monthly team challenges',
				'Dedicated account manager',
				'Usage analytics dashboard',
				'Flexible billing'
			],
			benefits: [
				'Improved employee wellness',
				'Reduced healthcare costs',
				'Higher productivity',
				'Better team morale',
				'Attractive hiring benefit'
			]
		},
		{
			id: 'growth',
			name: 'Growth Plan',
			description: 'Ideal for growing companies',
			minEmployees: 25,
			pricePerEmployee: 30,
			icon: '📈',
			popular: true,
			features: [
				'25-100 employees',
				'Premium gym access',
				'All group fitness classes',
				'Personal training credits',
				'Nutrition counseling',
				'Wellness seminars',
				'Team building events',
				'Priority booking system',
				'Custom corporate challenges',
				'Detailed reporting'
			],
			benefits: [
				'Comprehensive wellness program',
				'Reduced absenteeism',
				'Enhanced team building',
				'Competitive advantage in hiring',
				'Measurable ROI tracking'
			]
		},
		{
			id: 'enterprise',
			name: 'Enterprise Plan',
			description: 'Comprehensive solution for large organizations',
			minEmployees: 100,
			pricePerEmployee: 25,
			icon: '🏢',
			features: [
				'100+ employees',
				'Elite gym access',
				'Unlimited services',
				'On-site fitness assessments',
				'Corporate wellness programs',
				'Executive health screenings',
				'Lunch & learn sessions',
				'Dedicated corporate space',
				'Custom mobile app',
				'24/7 concierge support',
				'Quarterly business reviews'
			],
			benefits: [
				'Complete wellness ecosystem',
				'Significant cost savings',
				'Executive-level service',
				'Branded wellness experience',
				'Strategic partnership'
			]
		}
	];

	const corporateBenefits = [
		{
			icon: '💰',
			title: 'Cost Savings',
			description: 'Reduce healthcare costs and insurance premiums through improved employee wellness'
		},
		{
			icon: '📊',
			title: 'Performance Metrics',
			description: 'Track usage, engagement, and ROI with comprehensive analytics and reporting'
		},
		{
			icon: '🎯',
			title: 'Custom Programs',
			description: 'Tailored wellness initiatives designed specifically for your company culture'
		},
		{
			icon: '🤝',
			title: 'Team Building',
			description: 'Foster collaboration and team spirit through group challenges and events'
		}
	];

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
				<span class="text-sm font-medium text-white/70">🏢 For Businesses</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				CORPORATE
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					WELLNESS
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Invest in your team's health and productivity with our comprehensive corporate wellness
				programs. Flexible plans designed to fit any company size and budget.
			</p>
		</div>

		<!-- Corporate Benefits -->
		<div
			class="mb-20 grid transform grid-cols-1 gap-8 transition-all delay-400 duration-1000 md:grid-cols-2 lg:grid-cols-4 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each corporateBenefits as benefit, index}
				<div
					class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<div class="mb-4 text-4xl">{benefit.icon}</div>
					<h3 class="mb-3 text-lg font-bold text-white">{benefit.title}</h3>
					<p class="text-gray-300">{benefit.description}</p>
				</div>
			{/each}
		</div>

		<!-- Corporate Plans -->
		<div
			class="mb-20 grid transform grid-cols-1 gap-8 transition-all delay-600 duration-1000 lg:grid-cols-3 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each corporatePlans as plan, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10 {plan.popular
						? 'scale-105 border-white/30 shadow-2xl shadow-white/10'
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
							<p class="text-gray-400">{plan.description}</p>
						</div>

						<!-- Pricing -->
						<div class="mb-8 text-center">
							<div class="mb-2 text-5xl font-black text-white">
								${plan.pricePerEmployee}
							</div>
							<div class="text-lg text-gray-400">per employee/month</div>
							<div class="text-sm text-gray-500">Minimum {plan.minEmployees} employees</div>
						</div>

						<!-- Features -->
						<div class="mb-8">
							<h4 class="mb-4 text-lg font-semibold text-white">Plan includes:</h4>
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

						<!-- Benefits -->
						<div class="mb-8">
							<h4 class="mb-4 text-lg font-semibold text-white">Business benefits:</h4>
							<ul class="space-y-2">
								{#each plan.benefits as benefit}
									<li class="flex items-start space-x-2">
										<div class="mt-2 h-1 w-1 rounded-full bg-white/70"></div>
										<span class="text-sm text-gray-400">{benefit}</span>
									</li>
								{/each}
							</ul>
						</div>

						<!-- CTA Button -->
						<button
							class="w-full rounded-xl px-6 py-4 text-lg font-bold transition-all duration-300 {plan.popular
								? 'bg-white text-black hover:bg-gray-200'
								: 'border-2 border-white bg-transparent text-white hover:bg-white hover:text-black'}"
						>
							Get Quote
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

		<!-- ROI Calculator -->
		<div
			class="mb-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md"
			>
				<h3 class="mb-8 text-center text-3xl font-bold text-white">ROI Calculator</h3>
				<div class="grid grid-cols-1 gap-8 lg:grid-cols-2">
					<!-- Calculator Input -->
					<div>
						<h4 class="mb-4 text-xl font-semibold text-white">Your Company</h4>
						<div class="space-y-4">
							<div>
								<label class="mb-2 block text-sm font-medium text-gray-300">
									Number of Employees
								</label>
								<input
									type="number"
									value="50"
									class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white focus:border-white focus:outline-none focus:ring-2 focus:ring-white/20"
								/>
							</div>
							<div>
								<label class="mb-2 block text-sm font-medium text-gray-300">
									Average Salary ($)
								</label>
								<input
									type="number"
									value="65000"
									class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white focus:border-white focus:outline-none focus:ring-2 focus:ring-white/20"
								/>
							</div>
							<div>
								<label class="mb-2 block text-sm font-medium text-gray-300">
									Current Sick Days per Employee/Year
								</label>
								<input
									type="number"
									value="8"
									class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white focus:border-white focus:outline-none focus:ring-2 focus:ring-white/20"
								/>
							</div>
						</div>
					</div>

					<!-- ROI Results -->
					<div>
						<h4 class="mb-4 text-xl font-semibold text-white">Estimated Annual Savings</h4>
						<div class="space-y-4">
							<div class="rounded-xl border border-green-500/20 bg-green-500/10 p-4">
								<div class="text-2xl font-bold text-green-400">$45,000</div>
								<div class="text-sm text-gray-300">Reduced sick day costs</div>
							</div>
							<div class="rounded-xl border border-blue-500/20 bg-blue-500/10 p-4">
								<div class="text-2xl font-bold text-blue-400">$12,000</div>
								<div class="text-sm text-gray-300">Lower healthcare premiums</div>
							</div>
							<div class="rounded-xl border border-purple-500/20 bg-purple-500/10 p-4">
								<div class="text-2xl font-bold text-purple-400">$8,000</div>
								<div class="text-sm text-gray-300">Increased productivity</div>
							</div>
							<div class="rounded-xl border border-white/20 bg-white/10 p-4">
								<div class="text-3xl font-bold text-white">$65,000</div>
								<div class="text-sm text-gray-300">Total annual savings</div>
							</div>
						</div>
						<div class="mt-4 text-center">
							<div class="text-lg font-semibold text-white">ROI: 362%</div>
							<div class="text-sm text-gray-400">Program pays for itself in 3 months</div>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Case Studies -->
		<div
			class="mb-20 transform transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Success Stories</h3>
			<div class="grid grid-cols-1 gap-8 lg:grid-cols-3">
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-4 text-4xl">🚀</div>
					<h4 class="mb-3 text-lg font-bold text-white">TechStart Inc.</h4>
					<p class="mb-4 text-gray-300">
						45 employees saw 30% reduction in sick days and 25% improvement in job satisfaction after
						implementing our Growth Plan.
					</p>
					<div class="text-sm text-green-400">ROI: 340% in first year</div>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-4 text-4xl">📈</div>
					<h4 class="mb-3 text-lg font-bold text-white">Growth Corp</h4>
					<p class="mb-4 text-gray-300">
						150 employees experienced improved team cohesion and productivity through our
						comprehensive wellness program.
					</p>
					<div class="text-sm text-green-400">ROI: 285% in first year</div>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-4 text-4xl">🏢</div>
					<h4 class="mb-3 text-lg font-bold text-white">Enterprise Solutions</h4>
					<p class="mb-4 text-gray-300">
						500+ employees achieved significant healthcare cost reductions and improved employee
						retention rates.
					</p>
					<div class="text-sm text-green-400">ROI: 420% in first year</div>
				</div>
			</div>
		</div>

		<!-- CTA Section -->
		<div
			class="transform text-center transition-all delay-1200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-3xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md"
			>
				<h3 class="mb-4 text-2xl font-bold text-white">Ready to Transform Your Workplace?</h3>
				<p class="mb-6 text-gray-300">
					Let's discuss how a corporate wellness program can benefit your team and bottom line.
					Schedule a consultation with our corporate wellness experts.
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
						Download Brochure
					</button>
				</div>
			</div>
		</div>
	</div>
</section>