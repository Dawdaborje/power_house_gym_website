<script lang="ts">
	import { onMount } from 'svelte';

	let sectionRef: HTMLElement;
	let isVisible = false;
	let currentTestimonial = 0;

	const testimonials = [
		{
			id: 1,
			name: 'Sarah Thompson',
			location: 'Los Angeles, CA',
			image:
				'https://images.unsplash.com/photo-1494790108755-2616b332c27?ixlib=rb-4.0.3&auto=format&fit=crop&w=256&q=80',
			testimonial:
				'I have NEVER liked working out, especially in a gym! I LOVE Power House! All of the trainers are so encouraging and helpful. They have done a great job creating a community. I feel better than I have felt in years!',
			rating: 5,
			results: 'Lost 30lbs in 6 months',
			program: 'Hybrid Training'
		},
		{
			id: 2,
			name: 'Marcus Rodriguez',
			location: 'Miami, FL',
			image:
				'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=256&q=80',
			testimonial:
				"I was looking for a challenge and found that at Power House! I have seen more results in the 8 months I've been a member than the 3 years at my previous gym. The coaches are knowledgeable and make the workouts enjoyable!",
			rating: 5,
			results: 'Gained 15lbs muscle',
			program: 'Strength Training'
		},
		{
			id: 3,
			name: 'Emily Chen',
			location: 'New York, NY',
			image:
				'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&auto=format&fit=crop&w=256&q=80',
			testimonial:
				"For over a year, I have been a dedicated member of the Power House community. I've completely transformed my life. The newfound vitality extends beyond the gym – it energizes my entire lifestyle.",
			rating: 5,
			results: 'Improved overall fitness',
			program: 'Cardio + Strength'
		},
		{
			id: 4,
			name: 'David Kim',
			location: 'Seattle, WA',
			image:
				'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&auto=format&fit=crop&w=256&q=80',
			testimonial:
				"Power House is not just a place to work out and get fit... it's so much more. It's a big family, a support group of incredible non-judgmental people who will encourage you in your journey and celebrate your victories.",
			rating: 5,
			results: 'Mental & Physical transformation',
			program: 'All Programs'
		},
		{
			id: 5,
			name: 'Jessica Wu',
			location: 'Austin, TX',
			image:
				'https://images.unsplash.com/photo-1489424731084-a5d8b219a5bb?ixlib=rb-4.0.3&auto=format&fit=crop&w=256&q=80',
			testimonial:
				'Sessions have been fantastic! A varied range of people in the classes from beginners to really advanced. I can already see great results after 2 months – instructors are helpful, friendly and super supportive.',
			rating: 5,
			results: 'Strength & Confidence boost',
			program: 'Beginner Program'
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

		// Auto-cycle through testimonials
		const interval = setInterval(() => {
			currentTestimonial = (currentTestimonial + 1) % testimonials.length;
		}, 8000);

		return () => {
			if (sectionRef) {
				observer.unobserve(sectionRef);
			}
			clearInterval(interval);
		};
	});

	function nextTestimonial() {
		currentTestimonial = (currentTestimonial + 1) % testimonials.length;
	}

	function prevTestimonial() {
		currentTestimonial =
			currentTestimonial === 0 ? testimonials.length - 1 : currentTestimonial - 1;
	}
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
					<span class="text-sm font-medium text-white/70">💬 Member Stories</span>
				</div>

				<h2 class="mb-6 text-5xl font-black text-white md:text-6xl lg:text-7xl">
					FEEL THE <span
						class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
						>LOVE</span
					>
				</h2>

				<p class="mx-auto max-w-3xl text-xl leading-relaxed text-gray-300 md:text-2xl">
					Real stories from real members who've transformed their lives at Power House.
					<span class="font-semibold text-white">Their success is our inspiration.</span>
				</p>
			</div>
		</div>

		<!-- Testimonials Container -->
		<div
			class="relative mx-auto max-w-5xl transform transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<!-- Main Testimonial -->
			<div
				class="relative rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md md:p-12"
			>
				<!-- Quote Icon -->
				<div
					class="absolute top-8 left-8 flex h-16 w-16 items-center justify-center rounded-2xl bg-white/10"
				>
					<svg class="h-8 w-8 text-white" fill="currentColor" viewBox="0 0 24 24">
						<path
							d="M14.017 21v-7.391c0-5.704 3.731-9.57 8.983-10.609l.995 2.151c-2.432.917-3.995 3.638-3.995 5.849h4v10h-9.983zm-14.017 0v-7.391c0-5.704 3.748-9.57 9-10.609l.996 2.151c-2.433.917-3.996 3.638-3.996 5.849h4v10h-10z"
						/>
					</svg>
				</div>

				<!-- Testimonial Content -->
				<div class="pt-8">
					<div class="flex flex-col lg:flex-row lg:items-center lg:space-x-12">
						<!-- Testimonial Text -->
						<div class="mb-8 flex-1 lg:mb-0">
							<blockquote class="mb-8 text-xl leading-relaxed text-white md:text-2xl">
								"{testimonials[currentTestimonial].testimonial}"
							</blockquote>

							<!-- Rating -->
							<div class="mb-6 flex items-center space-x-1">
								{#each Array(5) as _, i}
									<svg class="h-6 w-6 text-yellow-400" fill="currentColor" viewBox="0 0 24 24">
										<path
											d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
										/>
									</svg>
								{/each}
							</div>

							<!-- Member Info -->
							<div class="flex items-center space-x-4">
								<img
									src={testimonials[currentTestimonial].image}
									alt={testimonials[currentTestimonial].name}
									class="h-16 w-16 rounded-full border-2 border-white/20 object-cover"
								/>
								<div>
									<h4 class="text-xl font-bold text-white">
										{testimonials[currentTestimonial].name}
									</h4>
									<p class="text-gray-300">
										{testimonials[currentTestimonial].location}
									</p>
								</div>
							</div>
						</div>

						<!-- Results Card -->
						<div class="lg:w-80">
							<div class="rounded-2xl bg-white p-6">
								<h5 class="mb-4 text-lg font-bold text-black">Transformation Results</h5>
								<div class="space-y-3">
									<div class="flex justify-between">
										<span class="text-gray-600">Program:</span>
										<span class="font-semibold text-black"
											>{testimonials[currentTestimonial].program}</span
										>
									</div>
									<div class="flex justify-between">
										<span class="text-gray-600">Results:</span>
										<span class="font-semibold text-black"
											>{testimonials[currentTestimonial].results}</span
										>
									</div>
									<div class="flex justify-between">
										<span class="text-gray-600">Rating:</span>
										<div class="flex items-center space-x-1">
											{#each Array(5) as _, i}
												<svg
													class="h-4 w-4 text-yellow-400"
													fill="currentColor"
													viewBox="0 0 24 24"
												>
													<path
														d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
													/>
												</svg>
											{/each}
										</div>
									</div>
								</div>
							</div>
						</div>
					</div>
				</div>
			</div>

			<!-- Navigation Controls -->
			<div class="mt-8 flex items-center justify-between">
				<!-- Previous Button -->
				<button
					on:click={prevTestimonial}
					class="flex h-12 w-12 items-center justify-center rounded-full bg-white/10 transition-colors duration-300 hover:bg-white/20"
				>
					<svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M15 19l-7-7 7-7"
						/>
					</svg>
				</button>

				<!-- Indicators -->
				<div class="flex space-x-3">
					{#each testimonials as _, index}
						<button
							on:click={() => (currentTestimonial = index)}
							class="h-3 w-3 rounded-full transition-all duration-300 {currentTestimonial === index
								? 'bg-white'
								: 'bg-white/30'}"
						></button>
					{/each}
				</div>

				<!-- Next Button -->
				<button
					on:click={nextTestimonial}
					class="flex h-12 w-12 items-center justify-center rounded-full bg-white/10 transition-colors duration-300 hover:bg-white/20"
				>
					<svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
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

		<!-- Testimonial Grid Preview -->
		<div
			class="mt-20 grid transform grid-cols-1 gap-6 transition-all delay-600 duration-1000 md:grid-cols-3 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each testimonials.slice(0, 3) as testimonial, index}
				<button
					on:click={() => (currentTestimonial = index)}
					class="rounded-2xl border border-white/10 bg-white/5 p-6 text-left transition-all duration-300 hover:bg-white/10 {currentTestimonial ===
					index
						? 'ring-2 ring-white/30'
						: ''}"
				>
					<div class="mb-4 flex items-center space-x-4">
						<img
							src={testimonial.image}
							alt={testimonial.name}
							class="h-12 w-12 rounded-full border border-white/20 object-cover"
						/>
						<div>
							<h6 class="text-sm font-semibold text-white">{testimonial.name}</h6>
							<p class="text-xs text-gray-400">{testimonial.location}</p>
						</div>
					</div>
					<p class="line-clamp-3 text-sm leading-relaxed text-gray-300">
						{testimonial.testimonial.slice(0, 120)}...
					</p>
				</button>
			{/each}
		</div>

		<!-- Call to Action -->
		<div
			class="mt-16 transform text-center transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-6 text-3xl font-bold text-white">Ready to write your success story?</h3>
			<div class="inline-flex flex-col gap-4 sm:flex-row">
				<button
					class="rounded-2xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
				>
					Start Your Transformation
				</button>
				<button
					class="rounded-2xl border-2 border-white px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
				>
					Read More Stories
				</button>
			</div>
		</div>
	</div>
</section>

<style>
	.line-clamp-3 {
		display: -webkit-box;
		-webkit-line-clamp: 3;
		-webkit-box-orient: vertical;
		overflow: hidden;
	}
</style>
