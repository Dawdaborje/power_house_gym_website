<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let selectedTrainer = '';
	let selectedService = '';
	let selectedDate = '';
	let selectedTime = '';

	const trainers = [
		{ id: 'marcus-steel', name: 'Marcus Steel', specialty: 'Strength Training', rate: '$120' },
		{ id: 'sarah-johnson', name: 'Sarah Johnson', specialty: 'Cardio & HIIT', rate: '$95' },
		{ id: 'alex-chen', name: 'Alex Chen', specialty: 'Functional Training', rate: '$110' },
		{ id: 'emma-wilson', name: 'Emma Wilson', specialty: 'Yoga & Wellness', rate: '$85' },
		{ id: 'mike-rodriguez', name: 'Mike Rodriguez', specialty: 'Powerlifting', rate: '$115' },
		{ id: 'lisa-park', name: 'Lisa Park', specialty: 'Nutrition Coaching', rate: '$90' }
	];

	const services = [
		{
			id: 'consultation',
			name: 'Initial Consultation',
			duration: '60 min',
			description: 'Assessment and goal setting'
		},
		{
			id: 'personal-training',
			name: 'Personal Training Session',
			duration: '60 min',
			description: 'One-on-one training'
		},
		{
			id: 'semi-private',
			name: 'Semi-Private Training',
			duration: '60 min',
			description: 'Training with a partner'
		},
		{
			id: 'nutrition-consult',
			name: 'Nutrition Consultation',
			duration: '45 min',
			description: 'Dietary planning and guidance'
		},
		{
			id: 'form-check',
			name: 'Form Analysis',
			duration: '30 min',
			description: 'Technique assessment and correction'
		}
	];

	const timeSlots = [
		'6:00 AM',
		'7:00 AM',
		'8:00 AM',
		'9:00 AM',
		'10:00 AM',
		'11:00 AM',
		'12:00 PM',
		'1:00 PM',
		'2:00 PM',
		'3:00 PM',
		'4:00 PM',
		'5:00 PM',
		'6:00 PM',
		'7:00 PM',
		'8:00 PM'
	];

	const packages = [
		{
			name: 'Starter Package',
			sessions: 4,
			price: '$320',
			originalPrice: '$380',
			savings: '$60',
			description: 'Perfect for beginners',
			features: [
				'4 Personal Training Sessions',
				'Initial Assessment',
				'Workout Plan',
				'Nutrition Guidance'
			]
		},
		{
			name: 'Transform Package',
			sessions: 8,
			price: '$600',
			originalPrice: '$760',
			savings: '$160',
			description: 'Most popular choice',
			features: [
				'8 Personal Training Sessions',
				'Body Composition Analysis',
				'Custom Meal Plan',
				'Progress Tracking',
				'24/7 Support'
			]
		},
		{
			name: 'Elite Package',
			sessions: 12,
			price: '$840',
			originalPrice: '$1140',
			savings: '$300',
			description: 'Maximum results',
			features: [
				'12 Personal Training Sessions',
				'Advanced Assessments',
				'Supplement Recommendations',
				'Monthly Check-ins',
				'Priority Scheduling'
			]
		}
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);

		// Set minimum date to today
		const today = new Date();
		const minDate = today.toISOString().split('T')[0];
		const dateInput = document.querySelector('input[type="date"]');
		if (dateInput) {
			dateInput.setAttribute('min', minDate);
		}
	});

	function handleBooking() {
		if (!selectedTrainer || !selectedService || !selectedDate || !selectedTime) {
			alert('Please fill in all required fields');
			return;
		}

		// Here you would normally send the booking data to your backend
		alert(
			'Booking request submitted! We will contact you within 24 hours to confirm your appointment.'
		);
	}
</script>

<section id="booking" class="bg-black pt-24 pb-12">
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
				<span class="text-sm font-medium text-white/70">📅 Book Your Session</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				START YOUR
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					JOURNEY
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Ready to take the next step? Book a session with one of our expert trainers and begin your
				transformation today.
			</p>
		</div>

		<div class="grid grid-cols-1 gap-12 lg:grid-cols-2">
			<!-- Booking Form -->
			<div
				class="transform transition-all delay-400 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md">
					<h3 class="mb-8 text-2xl font-bold text-white">Book Your Session</h3>

					<form class="space-y-6">
						<!-- Personal Info -->
						<div class="grid grid-cols-1 gap-4 sm:grid-cols-2">
							<div>
								<label class="mb-2 block text-sm font-medium text-white">First Name *</label>
								<input
									type="text"
									required
									class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white placeholder-gray-400 focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
									placeholder="Your first name"
								/>
							</div>
							<div>
								<label class="mb-2 block text-sm font-medium text-white">Last Name *</label>
								<input
									type="text"
									required
									class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white placeholder-gray-400 focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
									placeholder="Your last name"
								/>
							</div>
						</div>

						<div>
							<label class="mb-2 block text-sm font-medium text-white">Email *</label>
							<input
								type="email"
								required
								class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white placeholder-gray-400 focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
								placeholder="your.email@example.com"
							/>
						</div>

						<div>
							<label class="mb-2 block text-sm font-medium text-white">Phone *</label>
							<input
								type="tel"
								required
								class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white placeholder-gray-400 focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
								placeholder="(555) 123-4567"
							/>
						</div>

						<!-- Trainer Selection -->
						<div>
							<label class="mb-2 block text-sm font-medium text-white">Select Trainer *</label>
							<select
								bind:value={selectedTrainer}
								required
								class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
							>
								<option value="">Choose a trainer...</option>
								{#each trainers as trainer}
									<option value={trainer.id}>
										{trainer.name} - {trainer.specialty} ({trainer.rate}/hour)
									</option>
								{/each}
							</select>
						</div>

						<!-- Service Selection -->
						<div>
							<label class="mb-2 block text-sm font-medium text-white">Service Type *</label>
							<select
								bind:value={selectedService}
								required
								class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
							>
								<option value="">Choose a service...</option>
								{#each services as service}
									<option value={service.id}>
										{service.name} ({service.duration}) - {service.description}
									</option>
								{/each}
							</select>
						</div>

						<!-- Date & Time Selection -->
						<div class="grid grid-cols-1 gap-4 sm:grid-cols-2">
							<div>
								<label class="mb-2 block text-sm font-medium text-white">Preferred Date *</label>
								<input
									type="date"
									bind:value={selectedDate}
									required
									class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
								/>
							</div>
							<div>
								<label class="mb-2 block text-sm font-medium text-white">Preferred Time *</label>
								<select
									bind:value={selectedTime}
									required
									class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
								>
									<option value="">Choose a time...</option>
									{#each timeSlots as time}
										<option value={time}>{time}</option>
									{/each}
								</select>
							</div>
						</div>

						<!-- Goals/Notes -->
						<div>
							<label class="mb-2 block text-sm font-medium text-white">Fitness Goals & Notes</label>
							<textarea
								rows="4"
								class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white placeholder-gray-400 focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
								placeholder="Tell us about your fitness goals, experience level, any injuries or concerns..."
							></textarea>
						</div>

						<!-- Submit Button -->
						<button
							type="button"
							on:click={handleBooking}
							class="w-full rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-all duration-300 hover:scale-105 hover:bg-gray-200"
						>
							Book My Session
						</button>

						<p class="text-center text-sm text-gray-400">
							* We'll contact you within 24 hours to confirm your appointment
						</p>
					</form>
				</div>
			</div>

			<!-- Training Packages -->
			<div
				class="transform transition-all delay-600 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md">
					<h3 class="mb-8 text-2xl font-bold text-white">Training Packages</h3>

					<div class="space-y-6">
						{#each packages as pkg, index}
							<div
								class="group relative overflow-hidden rounded-2xl border border-white/10 bg-white/5 p-6 transition-all duration-300 hover:border-white/20 hover:bg-white/10"
								style="transition-delay: {index * 100}ms"
							>
								<!-- Savings Badge -->
								{#if pkg.savings}
									<div
										class="absolute top-4 right-4 rounded-full bg-green-500 px-3 py-1 text-xs font-bold text-white"
									>
										Save {pkg.savings}
									</div>
								{/if}

								<!-- Package Header -->
								<div class="mb-4">
									<h4 class="text-xl font-bold text-white">{pkg.name}</h4>
									<p class="text-gray-300">{pkg.description}</p>
								</div>

								<!-- Pricing -->
								<div class="mb-4 flex items-baseline space-x-2">
									<span class="text-3xl font-black text-white">{pkg.price}</span>
									{#if pkg.originalPrice}
										<span class="text-lg text-gray-400 line-through">{pkg.originalPrice}</span>
									{/if}
									<span class="text-sm text-gray-400">({pkg.sessions} sessions)</span>
								</div>

								<!-- Features -->
								<ul class="mb-6 space-y-2">
									{#each pkg.features as feature}
										<li class="flex items-center space-x-2">
											<svg class="h-4 w-4 text-green-400" fill="currentColor" viewBox="0 0 24 24">
												<path d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
											</svg>
											<span class="text-sm text-gray-300">{feature}</span>
										</li>
									{/each}
								</ul>

								<!-- CTA Button -->
								<button
									class="w-full rounded-xl border border-white/20 bg-white/10 px-6 py-3 text-sm font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
								>
									Select {pkg.name}
								</button>
							</div>
						{/each}
					</div>

					<!-- Contact Info -->
					<div class="mt-8 rounded-2xl border border-white/10 bg-white/5 p-6">
						<h4 class="mb-4 text-lg font-bold text-white">Have Questions?</h4>
						<div class="space-y-3">
							<div class="flex items-center space-x-3">
								<svg
									class="h-5 w-5 text-white/70"
									fill="none"
									stroke="currentColor"
									viewBox="0 0 24 24"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										stroke-width="2"
										d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
									/>
								</svg>
								<span class="text-gray-300">(555) 123-POWER</span>
							</div>
							<div class="flex items-center space-x-3">
								<svg
									class="h-5 w-5 text-white/70"
									fill="none"
									stroke="currentColor"
									viewBox="0 0 24 24"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										stroke-width="2"
										d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
									/>
								</svg>
								<span class="text-gray-300">trainers@powerhousegym.com</span>
							</div>
							<div class="flex items-center space-x-3">
								<svg
									class="h-5 w-5 text-white/70"
									fill="none"
									stroke="currentColor"
									viewBox="0 0 24 24"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										stroke-width="2"
										d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
									/>
								</svg>
								<span class="text-gray-300">Mon-Fri: 5 AM - 10 PM</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Guarantee Section -->
		<div
			class="mt-16 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-4 text-2xl font-bold text-white">Our Guarantee</h3>
				<p class="mb-6 text-lg text-gray-300">
					If you're not completely satisfied with your first session, we'll provide a full refund or
					match you with a different trainer. Your success is our commitment.
				</p>
				<div class="flex flex-wrap items-center justify-center gap-6">
					<div class="flex items-center space-x-2">
						<svg class="h-6 w-6 text-green-400" fill="currentColor" viewBox="0 0 24 24">
							<path d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
						</svg>
						<span class="font-medium text-white">100% Satisfaction Guarantee</span>
					</div>
					<div class="flex items-center space-x-2">
						<svg class="h-6 w-6 text-green-400" fill="currentColor" viewBox="0 0 24 24">
							<path d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
						</svg>
						<span class="font-medium text-white">Certified Professionals</span>
					</div>
					<div class="flex items-center space-x-2">
						<svg class="h-6 w-6 text-green-400" fill="currentColor" viewBox="0 0 24 24">
							<path d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
						</svg>
						<span class="font-medium text-white">Flexible Scheduling</span>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>
