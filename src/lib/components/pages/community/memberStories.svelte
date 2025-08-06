<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let selectedStory = 0;

	interface MemberStory {
		id: string;
		name: string;
		age: number;
		memberSince: string;
		image: string;
		transformation: string;
		story: string;
		achievement: string;
		quote: string;
		beforeAfter: {
			before: string;
			after: string;
		};
		tags: string[];
	}

	const memberStories: MemberStory[] = [
		{
			id: 'sarah-transformation',
			name: 'Sarah Martinez',
			age: 28,
			memberSince: '2022',
			image:
				'https://images.unsplash.com/photo-1494790108755-2616b612b34c?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			transformation: 'Lost 45lbs & gained confidence',
			story:
				'When I first walked into Power House, I was intimidated and unsure. The community here changed everything. From day one, members and trainers made me feel welcome. The group classes became my favorite part of the week, and the friendships I made kept me motivated even on tough days.',
			achievement: 'Completed first 5K race',
			quote:
				'Power House gave me more than a fit body - it gave me a family and unshakeable confidence.',
			beforeAfter: {
				before: 'Struggled with self-confidence',
				after: 'Leading group fitness classes'
			},
			tags: ['Weight Loss', 'Confidence', 'Community Leader']
		},
		{
			id: 'mike-strength',
			name: 'Mike Johnson',
			age: 35,
			memberSince: '2020',
			image:
				'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			transformation: 'From couch to powerlifter',
			story:
				"Three years ago, I was 50lbs overweight and hadn't exercised in years. The Power House community didn't just help me get in shape - they helped me discover a passion for powerlifting. Now I compete nationally and mentor new members.",
			achievement: '500lb deadlift & national competition',
			quote:
				'The support here is unreal. When I hit my first 400lb deadlift, the whole gym erupted in cheers.',
			beforeAfter: {
				before: 'Sedentary lifestyle, low energy',
				after: 'Competitive powerlifter & mentor'
			},
			tags: ['Strength Training', 'Competition', 'Mentorship']
		},
		{
			id: 'lisa-wellness',
			name: 'Lisa Chen',
			age: 42,
			memberSince: '2021',
			image:
				'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			transformation: 'Mind-body wellness journey',
			story:
				'After a stressful divorce, I was struggling with anxiety and depression. The Power House community became my sanctuary. Through yoga classes and supportive friendships, I found inner peace and strength I never knew I had.',
			achievement: 'Became certified yoga instructor',
			quote: 'This place saved my life. The healing power of this community is something special.',
			beforeAfter: {
				before: 'High stress, anxiety issues',
				after: 'Peaceful, balanced lifestyle'
			},
			tags: ['Mental Health', 'Yoga', 'Life Balance']
		},
		{
			id: 'james-comeback',
			name: 'James Williams',
			age: 55,
			memberSince: '2019',
			image:
				'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			transformation: 'Post-injury comeback',
			story:
				"After a major back injury, doctors said I'd never lift again. The Power House community proved them wrong. With patient guidance from trainers and constant encouragement from fellow members, I not only recovered but became stronger than ever.",
			achievement: 'Full recovery & personal bests',
			quote:
				"They believed in me when I couldn't believe in myself. That's the Power House difference.",
			beforeAfter: {
				before: 'Major back injury, limited mobility',
				after: 'Pain-free & stronger than before'
			},
			tags: ['Injury Recovery', 'Resilience', 'Inspiration']
		}
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);

		// Auto-rotate stories
		const interval = setInterval(() => {
			selectedStory = (selectedStory + 1) % memberStories.length;
		}, 8000);

		return () => clearInterval(interval);
	});

	function selectStory(index: number) {
		selectedStory = index;
	}
</script>

<section id="stories" class="bg-black py-24">
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
				<span class="text-sm font-medium text-white/70">💪 Real Transformations</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				MEMBER
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					STORIES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Every member has a unique journey. Here are just a few stories of transformation, triumph,
				and the power of community support.
			</p>
		</div>

		<!-- Featured Story -->
		<div
			class="mb-16 transform transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md"
			>
				{#each memberStories as story, index}
					<div
						class="absolute inset-0 transition-all duration-700 {index === selectedStory
							? 'translate-x-0 opacity-100'
							: index < selectedStory
								? '-translate-x-full opacity-0'
								: 'translate-x-full opacity-0'}"
					>
						<div class="grid grid-cols-1 lg:grid-cols-2">
							<!-- Story Content -->
							<div class="p-8 lg:p-12">
								<!-- Member Info -->
								<div class="mb-8">
									<h3 class="mb-2 text-3xl font-bold text-white">{story.name}</h3>
									<p class="text-gray-400">Age {story.age} • Member since {story.memberSince}</p>
									<div class="mt-3 inline-block rounded-full bg-white/10 px-4 py-1">
										<span class="text-sm font-medium text-white">{story.transformation}</span>
									</div>
								</div>

								<!-- Story Quote -->
								<blockquote class="mb-8 text-2xl leading-relaxed font-medium text-white italic">
									"{story.quote}"
								</blockquote>

								<!-- Story Content -->
								<p class="mb-8 text-lg leading-relaxed text-gray-300">
									{story.story}
								</p>

								<!-- Before/After -->
								<div class="mb-8 grid grid-cols-1 gap-4 md:grid-cols-2">
									<div class="rounded-xl border border-red-500/20 bg-red-500/10 p-4">
										<h4 class="mb-2 font-semibold text-red-400">Before</h4>
										<p class="text-sm text-gray-300">{story.beforeAfter.before}</p>
									</div>
									<div class="rounded-xl border border-green-500/20 bg-green-500/10 p-4">
										<h4 class="mb-2 font-semibold text-green-400">After</h4>
										<p class="text-sm text-gray-300">{story.beforeAfter.after}</p>
									</div>
								</div>

								<!-- Achievement -->
								<div class="mb-8 rounded-xl border border-yellow-500/20 bg-yellow-500/10 p-4">
									<h4 class="mb-2 font-semibold text-yellow-400">Key Achievement</h4>
									<p class="text-gray-300">{story.achievement}</p>
								</div>

								<!-- Tags -->
								<div class="flex flex-wrap gap-2">
									{#each story.tags as tag}
										<span
											class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white/80"
										>
											{tag}
										</span>
									{/each}
								</div>
							</div>

							<!-- Member Image -->
							<div class="relative h-96 lg:h-auto">
								<img src={story.image} alt={story.name} class="h-full w-full object-cover" />
								<div
									class="absolute inset-0 bg-gradient-to-t from-black/40 via-transparent to-transparent lg:bg-gradient-to-l lg:from-black/40"
								></div>
							</div>
						</div>
					</div>
				{/each}

				<!-- Navigation -->
				<div class="absolute right-6 bottom-6 left-6 flex items-center justify-between">
					<!-- Story Indicators -->
					<div class="flex space-x-2">
						{#each memberStories as _, index}
							<button
								on:click={() => selectStory(index)}
								class="h-3 w-3 rounded-full transition-all duration-300 {index === selectedStory
									? 'scale-125 bg-white'
									: 'bg-white/30 hover:bg-white/50'}"
							></button>
						{/each}
					</div>

					<!-- Auto-play indicator -->
					<div class="flex items-center space-x-2 text-white/70">
						<svg class="h-4 w-4 animate-spin" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"
							/>
						</svg>
						<span class="text-xs">Auto-changing</span>
					</div>
				</div>
			</div>
		</div>

		<!-- Member Stories Grid -->
		<div
			class="transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-8 text-center text-3xl font-bold text-white">More Success Stories</h3>
			<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4">
				{#each memberStories as story, index}
					<div
						class="group cursor-pointer rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md transition-all duration-300 hover:border-white/20 hover:bg-white/10"
						on:click={() => selectStory(index)}
						style="transition-delay: {index * 100}ms"
					>
						<!-- Member Image -->
						<div class="mx-auto mb-4 h-20 w-20 overflow-hidden rounded-full">
							<img src={story.image} alt={story.name} class="h-full w-full object-cover" />
						</div>

						<!-- Member Info -->
						<div class="text-center">
							<h4 class="mb-1 font-semibold text-white">{story.name}</h4>
							<p class="mb-3 text-sm text-gray-400">Member since {story.memberSince}</p>
							<p class="mb-4 text-sm font-medium text-white">{story.transformation}</p>
							<p class="text-xs text-gray-300 italic">"{story.quote.substring(0, 60)}..."</p>
						</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- Community Impact -->
		<div
			class="mt-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-6 text-3xl font-bold text-white">Community Impact</h3>
				<div class="grid grid-cols-1 gap-6 md:grid-cols-3">
					<div>
						<div class="mb-2 text-4xl font-black text-white">500+</div>
						<div class="text-gray-300">Transformation Stories</div>
					</div>
					<div>
						<div class="mb-2 text-4xl font-black text-white">15K+</div>
						<div class="text-gray-300">Pounds Lost Together</div>
					</div>
					<div>
						<div class="mb-2 text-4xl font-black text-white">98%</div>
						<div class="text-gray-300">Would Recommend</div>
					</div>
				</div>
				<div class="mt-8">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Share Your Story
					</button>
				</div>
			</div>
		</div>
	</div>
</section>
