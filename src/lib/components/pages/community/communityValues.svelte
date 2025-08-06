<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	const values = [
		{
			icon: '🤝',
			title: 'Support & Encouragement',
			description:
				'Every member matters. We celebrate victories together and provide support during challenges.',
			examples: ['Workout buddies', 'Goal accountability', 'Motivational community']
		},
		{
			icon: '🌟',
			title: 'Inclusive Excellence',
			description:
				'All fitness levels, backgrounds, and goals are welcomed. Excellence means being the best version of yourself.',
			examples: ['Beginner-friendly environment', 'Diverse membership', 'Personal growth focus']
		},
		{
			icon: '💪',
			title: 'Strength in Unity',
			description:
				'Individual strength is amplified when we work together. Our collective energy drives everyone forward.',
			examples: ['Group challenges', 'Team workouts', 'Community events']
		},
		{
			icon: '🎯',
			title: 'Goal-Oriented Culture',
			description:
				'We believe in setting ambitious goals and supporting each other in achieving them.',
			examples: ['Personal milestones', 'Community challenges', 'Achievement recognition']
		}
	];

	const communityGuidelines = [
		{
			title: 'Respect & Kindness',
			description:
				'Treat every member with respect, regardless of their fitness level or background.',
			icon: '❤️'
		},
		{
			title: 'Encourage Others',
			description:
				'A simple "you got this!" can make someone\'s day. Spread positivity and motivation.',
			icon: '📣'
		},
		{
			title: 'Share Knowledge',
			description:
				'Help fellow members with tips, techniques, and experiences. Learning together makes us stronger.',
			icon: '🧠'
		},
		{
			title: 'Celebrate Wins',
			description:
				'No achievement is too small. Celebrate your own victories and cheer for others.',
			icon: '🎉'
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
				<span class="text-sm font-medium text-white/70">⭐ Our Foundation</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				COMMUNITY
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					VALUES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Our values shape every interaction, every workout, and every relationship in our community.
				They're not just words on a wall - they're lived every day.
			</p>
		</div>

		<!-- Core Values -->
		<div
			class="mb-20 grid transform grid-cols-1 gap-8 transition-all delay-400 duration-1000 md:grid-cols-2 lg:grid-cols-4 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each values as value, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10"
					style="transition-delay: {index * 150}ms"
				>
					<!-- Icon -->
					<div class="mb-6 text-5xl">{value.icon}</div>

					<!-- Title -->
					<h3 class="mb-4 text-xl font-bold text-white transition-colors group-hover:text-gray-200">
						{value.title}
					</h3>

					<!-- Description -->
					<p class="mb-6 leading-relaxed text-gray-300">
						{value.description}
					</p>

					<!-- Examples -->
					<div class="space-y-2">
						{#each value.examples as example}
							<div class="flex items-center justify-center space-x-2">
								<div class="h-1.5 w-1.5 rounded-full bg-white/60"></div>
								<span class="text-sm text-gray-400">{example}</span>
							</div>
						{/each}
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

		<!-- Community Guidelines -->
		<div
			class="transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mx-auto max-w-4xl">
				<h3 class="mb-12 text-center text-3xl font-bold text-white">How We Support Each Other</h3>

				<div class="grid grid-cols-1 gap-6 md:grid-cols-2">
					{#each communityGuidelines as guideline, index}
						<div
							class="flex items-start space-x-4 rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md transition-all duration-300 hover:border-white/20 hover:bg-white/10"
							style="transition-delay: {200 + index * 100}ms"
						>
							<!-- Icon -->
							<div class="flex-shrink-0 text-3xl">{guideline.icon}</div>

							<!-- Content -->
							<div>
								<h4 class="mb-2 text-lg font-bold text-white">{guideline.title}</h4>
								<p class="text-gray-300">{guideline.description}</p>
							</div>
						</div>
					{/each}
				</div>
			</div>
		</div>

		<!-- Community Pledge -->
		<div
			class="mt-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/20 bg-gradient-to-r from-white/10 to-white/5 p-8 text-center backdrop-blur-md md:p-12"
			>
				<h3 class="mb-6 text-3xl font-bold text-white">The Power House Pledge</h3>
				<blockquote class="mb-8 text-xl leading-relaxed text-gray-300 italic">
					"We commit to supporting each other's journey, celebrating every victory, and creating an
					environment where everyone feels valued, motivated, and empowered to reach their full
					potential."
				</blockquote>
				<div class="flex items-center justify-center space-x-4">
					<div class="h-px w-16 bg-white/30"></div>
					<span class="text-white/70">Together We Rise</span>
					<div class="h-px w-16 bg-white/30"></div>
				</div>
			</div>
		</div>

		<!-- Join Community CTA -->
		<div
			class="mt-16 transform text-center transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mx-auto max-w-2xl">
				<h4 class="mb-4 text-2xl font-bold text-white">Ready to be part of something special?</h4>
				<p class="mb-6 text-gray-300">
					Join a community that will support your journey, celebrate your wins, and help you become
					the strongest version of yourself.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Join Our Community
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Visit the Gym
					</button>
				</div>
			</div>
		</div>
	</div>
</section>
