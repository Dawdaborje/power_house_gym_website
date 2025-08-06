<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let currentTestimonial = 0;

	interface Testimonial {
		id: string;
		clientName: string;
		clientImage: string;
		trainer: string;
		specialty: string;
		testimonial: string;
		results: string;
		duration: string;
		rating: number;
	}

	const testimonials: Testimonial[] = [
		{
			id: '1',
			clientName: 'Jessica Chen',
			clientImage:
				'https://images.unsplash.com/photo-1494790108755-2616b612b34c?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80',
			trainer: 'Marcus Steel',
			specialty: 'Strength Training',
			testimonial:
				'Marcus completely transformed my relationship with lifting. I went from being intimidated by the weight room to deadlifting 200lbs! His patient coaching and perfect form corrections made all the difference.',
			results: 'Lost 25lbs, gained 15lbs muscle',
			duration: '6 months',
			rating: 5
		},
		{
			id: '2',
			clientName: 'David Rodriguez',
			clientImage:
				'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80',
			trainer: 'Sarah Johnson',
			specialty: 'HIIT & Cardio',
			testimonial:
				"Sarah's HIIT classes are incredible! She pushes you to your limits while keeping it fun and motivating. I've never been in better cardiovascular shape in my life.",
			results: 'Improved VO2 max by 30%',
			duration: '4 months',
			rating: 5
		},
		{
			id: '3',
			clientName: 'Maria Lopez',
			clientImage:
				'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80',
			trainer: 'Emma Wilson',
			specialty: 'Yoga & Wellness',
			testimonial:
				'Emma helped me find balance in both my body and mind. Her yoga classes are transformative, and the meditation techniques she taught me have reduced my stress levels dramatically.',
			results: 'Increased flexibility by 40%',
			duration: '8 months',
			rating: 5
		},
		{
			id: '4',
			clientName: 'James Kim',
			clientImage:
				'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80',
			trainer: 'Alex Chen',
			specialty: 'Functional Training',
			testimonial:
				"Alex's functional training approach fixed my chronic back pain and made me move like an athlete again. His expertise in movement patterns is unmatched.",
			results: 'Eliminated chronic pain',
			duration: '3 months',
			rating: 5
		},
		{
			id: '5',
			clientName: 'Lisa Thompson',
			clientImage:
				'https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80',
			trainer: 'Lisa Park',
			specialty: 'Nutrition Coaching',
			testimonial:
				'Lisa completely changed how I think about food. No more crash diets or guilt - just sustainable, healthy habits that fit my lifestyle perfectly.',
			results: 'Lost 30lbs sustainably',
			duration: '5 months',
			rating: 5
		},
		{
			id: '6',
			clientName: 'Robert Johnson',
			clientImage:
				'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80',
			trainer: 'Mike Rodriguez',
			specialty: 'Powerlifting',
			testimonial:
				'Mike coached me to my first powerlifting competition and I hit PRs in all three lifts! His technical knowledge and competition experience were invaluable.',
			results: '50lb+ PR across all lifts',
			duration: '12 months',
			rating: 5
		}
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);

		// Auto-rotate testimonials
		const interval = setInterval(() => {
			currentTestimonial = (currentTestimonial + 1) % testimonials.length;
		}, 5000);

		return () => clearInterval(interval);
	});

	function nextTestimonial() {
		currentTestimonial = (currentTestimonial + 1) % testimonials.length;
	}

	function prevTestimonial() {
		currentTestimonial =
			currentTestimonial === 0 ? testimonials.length - 1 : currentTestimonial - 1;
	}

	function goToTestimonial(index: number) {
		currentTestimonial = index;
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
				<span class="text-sm font-medium text-white/70">💬 Client Success</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				SUCCESS
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					STORIES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Real results from real people. See how our expert trainers have helped members achieve their
				fitness goals and transform their lives.
			</p>
		</div>

		<!-- Featured Testimonial -->
		<div
			class="mb-16 transform transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md"
			>
				{#each testimonials as testimonial, index}
					<div
						class="absolute inset-0 transition-all duration-500 {index === currentTestimonial
							? 'translate-x-0 opacity-100'
							: index < currentTestimonial
								? '-translate-x-full opacity-0'
								: 'translate-x-full opacity-0'}"
					>
						<div class="grid grid-cols-1 lg:grid-cols-2">
							<!-- Content -->
							<div class="p-8 lg:p-12">
								<!-- Rating -->
								<div class="mb-6 flex items-center space-x-1">
									{#each Array(testimonial.rating) as _}
										<svg class="h-6 w-6 text-yellow-400" fill="currentColor" viewBox="0 0 24 24">
											<path
												d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
											/>
										</svg>
									{/each}
								</div>

								<!-- Testimonial Text -->
								<blockquote class="mb-8 text-xl leading-relaxed text-gray-300 italic">
									"{testimonial.testimonial}"
								</blockquote>

								<!-- Client Info -->
								<div class="mb-6">
									<h4 class="text-2xl font-bold text-white">{testimonial.clientName}</h4>
									<p class="text-gray-400">Training with {testimonial.trainer}</p>
									<p class="text-sm text-white/70">
										{testimonial.specialty} • {testimonial.duration}
									</p>
								</div>

								<!-- Results -->
								<div class="rounded-xl border border-white/10 bg-white/5 p-4">
									<h5 class="mb-2 font-semibold text-white">Results Achieved:</h5>
									<p class="text-gray-300">{testimonial.results}</p>
								</div>
							</div>

							<!-- Client Image -->
							<div class="relative h-96 lg:h-auto">
								<img
									src={testimonial.clientImage}
									alt={testimonial.clientName}
									class="h-full w-full object-cover"
								/>
								<div
									class="absolute inset-0 bg-gradient-to-t from-black/30 via-transparent to-transparent lg:bg-gradient-to-r lg:from-black/30"
								></div>
							</div>
						</div>
					</div>
				{/each}

				<!-- Navigation Controls -->
				<div class="absolute right-6 bottom-6 left-6 flex items-center justify-between">
					<!-- Dots Indicator -->
					<div class="flex space-x-2">
						{#each testimonials as _, index}
							<button
								on:click={() => goToTestimonial(index)}
								class="h-3 w-3 rounded-full transition-all duration-300 {index ===
								currentTestimonial
									? 'scale-125 bg-white'
									: 'bg-white/30 hover:bg-white/50'}"
							></button>
						{/each}
					</div>

					<!-- Arrow Controls -->
					<div class="flex space-x-4">
						<button
							on:click={prevTestimonial}
							class="rounded-full bg-white/10 p-2 text-white backdrop-blur-md transition-all duration-300 hover:bg-white/20"
						>
							<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M15 19l-7-7 7-7"
								/>
							</svg>
						</button>
						<button
							on:click={nextTestimonial}
							class="rounded-full bg-white/10 p-2 text-white backdrop-blur-md transition-all duration-300 hover:bg-white/20"
						>
							<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M9 5l7 7-7 7"
								/>
							</svg>
						</button>
					</div>
				</div>
			</div>
		</div>

		<!-- Testimonials Grid -->
		<div
			class="transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-8 text-center text-3xl font-bold text-white">More Success Stories</h3>
			<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-3">
				{#each testimonials.slice(0, 6) as testimonial, index}
					<div
						class="group cursor-pointer rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md transition-all duration-300 hover:border-white/20 hover:bg-white/10"
						on:click={() => goToTestimonial(index)}
						style="transition-delay: {index * 100}ms"
					>
						<!-- Client -->
						<div class="mb-4 flex items-center space-x-4">
							<img
								src={testimonial.clientImage}
								alt={testimonial.clientName}
								class="h-12 w-12 rounded-full object-cover"
							/>
							<div>
								<h4 class="font-semibold text-white">{testimonial.clientName}</h4>
								<p class="text-sm text-gray-400">with {testimonial.trainer}</p>
							</div>
						</div>

						<!-- Rating -->
						<div class="mb-3 flex items-center space-x-1">
							{#each Array(testimonial.rating) as _}
								<svg class="h-4 w-4 text-yellow-400" fill="currentColor" viewBox="0 0 24 24">
									<path
										d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
									/>
								</svg>
							{/each}
						</div>

						<!-- Testimonial Preview -->
						<p class="mb-4 text-sm leading-relaxed text-gray-300">
							"{testimonial.testimonial.substring(0, 120)}..."
						</p>

						<!-- Results -->
						<div class="rounded-lg bg-white/5 p-3">
							<p class="text-xs font-medium text-white">{testimonial.results}</p>
							<p class="text-xs text-gray-400">{testimonial.duration}</p>
						</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- CTA Section -->
		<div
			class="mt-16 transform text-center transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-2xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md"
			>
				<h4 class="mb-4 text-2xl font-bold text-white">Ready to write your success story?</h4>
				<p class="mb-6 text-gray-300">
					Join hundreds of members who have transformed their lives with our expert trainers.
				</p>
				<button
					class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
				>
					Start Your Transformation
				</button>
			</div>
		</div>
	</div>
</section>
