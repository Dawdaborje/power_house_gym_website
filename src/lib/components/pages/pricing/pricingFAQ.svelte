<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let openQuestion: string | null = null;

	interface FAQ {
		id: string;
		question: string;
		answer: string;
		category: 'membership' | 'billing' | 'features' | 'cancellation';
	}

	const faqs: FAQ[] = [
		{
			id: 'membership-1',
			category: 'membership',
			question: 'Can I upgrade or downgrade my membership plan?',
			answer: 'Yes! You can upgrade your membership at any time and it takes effect immediately. For downgrades, the change will take effect at your next billing cycle. There are no fees for plan changes.'
		},
		{
			id: 'billing-1',
			category: 'billing',
			question: 'What payment methods do you accept?',
			answer: 'We accept all major credit cards (Visa, Mastercard, American Express), debit cards, and bank transfers. For corporate accounts, we also accept ACH transfers and can provide invoicing options.'
		},
		{
			id: 'membership-2',
			category: 'membership',
			question: 'Is there a long-term contract requirement?',
			answer: 'No! All our memberships are month-to-month with no long-term contracts. You can cancel anytime with 30 days notice. We believe in earning your membership every month.'
		},
		{
			id: 'features-1',
			category: 'features',
			question: 'What\'s included in the 7-day free trial?',
			answer: 'Your free trial includes full access to all gym facilities, equipment, group fitness classes, locker rooms, and our mobile app. It\'s essentially a Premium membership experience for 7 days at no cost.'
		},
		{
			id: 'billing-2',
			category: 'billing',
			question: 'When am I charged for my membership?',
			answer: 'You\'re charged on the same date each month that you signed up. For example, if you join on the 15th, you\'ll be charged on the 15th of each month. We send email reminders 3 days before each billing date.'
		},
		{
			id: 'cancellation-1',
			category: 'cancellation',
			question: 'How do I cancel my membership?',
			answer: 'You can cancel your membership through your online account, our mobile app, or by visiting our front desk. We require 30 days notice, so if you cancel on the 10th, your membership ends on the 10th of the following month.'
		},
		{
			id: 'features-2',
			category: 'features',
			question: 'Can I bring guests to the gym?',
			answer: 'Guest privileges vary by plan. Basic members can purchase day passes for $15. Premium members get 2 guest passes per month. Elite members enjoy unlimited guest passes. All guests must sign a waiver and be accompanied by the member.'
		},
		{
			id: 'billing-3',
			category: 'billing',
			question: 'Are there any hidden fees or additional costs?',
			answer: 'Absolutely not! Our pricing is completely transparent. The only additional costs are optional add-on services you choose (like personal training or massage therapy) and replacement key fobs if lost ($10 fee).'
		},
		{
			id: 'membership-3',
			category: 'membership',
			question: 'Can I freeze or pause my membership?',
			answer: 'Yes, we offer membership freezes for medical reasons, extended travel, or other qualifying circumstances. Freezes can be up to 3 months per year with proper documentation. A small administrative fee of $10/month applies during the freeze period.'
		},
		{
			id: 'features-3',
			category: 'features',
			question: 'What happens if I exceed the class booking limit?',
			answer: 'Premium and Elite members have unlimited class bookings. Basic members would need to upgrade or pay drop-in rates ($20/class). However, we rarely see this happen as our class schedule is designed to accommodate all members.'
		},
		{
			id: 'cancellation-2',
			category: 'cancellation',
			question: 'Is there a cancellation fee?',
			answer: 'No cancellation fees! We only require 30 days notice. If you have any outstanding balances for add-on services, those would need to be settled, but there\'s no penalty for ending your membership.'
		},
		{
			id: 'billing-4',
			category: 'billing',
			question: 'Do you offer student or senior discounts?',
			answer: 'Yes! We offer 15% off all membership plans for full-time students (with valid ID) and seniors 65+. Military members and first responders also receive a 20% discount. These discounts can be applied at signup or retroactively.'
		}
	];

	const categories = {
		membership: { name: 'Membership', icon: '🏋️‍♂️', color: 'text-blue-400' },
		billing: { name: 'Billing', icon: '💳', color: 'text-green-400' },
		features: { name: 'Features', icon: '⚡', color: 'text-yellow-400' },
		cancellation: { name: 'Cancellation', icon: '❌', color: 'text-red-400' }
	};

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function toggleQuestion(questionId: string) {
		openQuestion = openQuestion === questionId ? null : questionId;
	}

	function getQuestionsByCategory(category: string) {
		return faqs.filter(faq => faq.category === category);
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
				<span class="text-sm font-medium text-white/70">❓ Got Questions?</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				FREQUENTLY ASKED
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					QUESTIONS
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Find answers to common questions about our membership plans, billing, and policies. Can't
				find what you're looking for? Our team is here to help.
			</p>
		</div>

		<!-- FAQ Categories -->
		<div
			class="mb-12 flex transform flex-wrap justify-center gap-4 transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each Object.entries(categories) as [key, category]}
				<div class="flex items-center space-x-2 rounded-full border border-white/10 bg-white/5 px-4 py-2">
					<span class="text-lg">{category.icon}</span>
					<span class="text-sm font-medium text-white">{category.name}</span>
					<span class="rounded-full bg-white/20 px-2 py-0.5 text-xs text-white">
						{getQuestionsByCategory(key).length}
					</span>
				</div>
			{/each}
		</div>

		<!-- FAQ Grid -->
		<div
			class="grid transform grid-cols-1 gap-8 transition-all delay-600 duration-1000 lg:grid-cols-2 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each faqs as faq, index}
				<div
					class="rounded-2xl border border-white/10 bg-white/5 backdrop-blur-md transition-all duration-300 hover:bg-white/10"
					style="transition-delay: {index * 50}ms"
				>
					<button
						on:click={() => toggleQuestion(faq.id)}
						class="w-full p-6 text-left transition-all duration-300"
					>
						<div class="flex items-start justify-between">
							<div class="flex items-start space-x-3">
								<div class="flex-shrink-0 text-lg {categories[faq.category].color}">
									{categories[faq.category].icon}
								</div>
								<div class="flex-1">
									<h3 class="text-lg font-semibold text-white group-hover:text-gray-200">
										{faq.question}
									</h3>
									<div class="mt-1 text-sm {categories[faq.category].color}">
										{categories[faq.category].name}
									</div>
								</div>
							</div>
							<div class="flex-shrink-0">
								<svg
									class="h-5 w-5 text-white transition-transform duration-300 {openQuestion === faq.id
										? 'rotate-180'
										: ''}"
									fill="none"
									stroke="currentColor"
									viewBox="0 0 24 24"
								>
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
								</svg>
							</div>
						</div>
					</button>

					<!-- Answer -->
					<div
						class="overflow-hidden transition-all duration-300 {openQuestion === faq.id
							? 'max-h-96 opacity-100'
							: 'max-h-0 opacity-0'}"
					>
						<div class="border-t border-white/10 p-6 pt-4">
							<p class="leading-relaxed text-gray-300">{faq.answer}</p>
						</div>
					</div>
				</div>
			{/each}
		</div>

		<!-- Contact Support -->
		<div
			class="mt-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-3xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-4 text-2xl font-bold text-white">Still Have Questions?</h3>
				<p class="mb-6 text-gray-300">
					Our friendly team is here to help! Get in touch and we'll answer any questions you have
					about memberships, pricing, or our facilities.
				</p>

				<!-- Contact Options -->
				<div class="mb-8 grid grid-cols-1 gap-4 md:grid-cols-3">
					<div class="rounded-xl border border-white/10 bg-white/5 p-4">
						<div class="mb-2 text-2xl">💬</div>
						<div class="font-semibold text-white">Live Chat</div>
						<div class="text-sm text-gray-400">Available 7am-10pm daily</div>
					</div>
					<div class="rounded-xl border border-white/10 bg-white/5 p-4">
						<div class="mb-2 text-2xl">📞</div>
						<div class="font-semibold text-white">Call Us</div>
						<div class="text-sm text-gray-400">(555) 123-4567</div>
					</div>
					<div class="rounded-xl border border-white/10 bg-white/5 p-4">
						<div class="mb-2 text-2xl">✉️</div>
						<div class="font-semibold text-white">Email</div>
						<div class="text-sm text-gray-400">support@powerhousegym.com</div>
					</div>
				</div>

				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Start Live Chat
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Schedule Call Back
					</button>
				</div>
			</div>
		</div>

		<!-- Quick Tips -->
		<div
			class="mt-16 transform transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
				<h4 class="mb-4 text-lg font-bold text-white">💡 Quick Tips</h4>
				<div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-4">
					<div class="text-center">
						<div class="mb-2 text-2xl">🎯</div>
						<div class="text-sm font-medium text-white">Start with Basic</div>
						<div class="text-xs text-gray-400">You can always upgrade later</div>
					</div>
					<div class="text-center">
						<div class="mb-2 text-2xl">📅</div>
						<div class="text-sm font-medium text-white">Try Before You Buy</div>
						<div class="text-xs text-gray-400">7-day free trial available</div>
					</div>
					<div class="text-center">
						<div class="mb-2 text-2xl">💰</div>
						<div class="text-sm font-medium text-white">Annual Savings</div>
						<div class="text-xs text-gray-400">Save 20% with yearly billing</div>
					</div>
					<div class="text-center">
						<div class="mb-2 text-2xl">🎓</div>
						<div class="text-sm font-medium text-white">Special Discounts</div>
						<div class="text-xs text-gray-400">Students, seniors, military</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>