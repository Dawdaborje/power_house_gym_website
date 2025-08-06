<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let selectedChallenge = 'current';

	interface Challenge {
		id: string;
		title: string;
		description: string;
		type: 'strength' | 'cardio' | 'consistency' | 'team';
		duration: string;
		participants: number;
		maxParticipants?: number;
		startDate: Date;
		endDate: Date;
		status: 'upcoming' | 'active' | 'completed';
		prize: string;
		rules: string[];
		leaderboard?: {
			rank: number;
			name: string;
			score: string;
			avatar: string;
		}[];
		progress?: {
			current: number;
			target: number;
			unit: string;
		};
	}

	const challenges: Challenge[] = [
		{
			id: 'deadlift-december',
			title: 'Deadlift December',
			description: 'Push your limits and achieve a new deadlift personal record this month!',
			type: 'strength',
			duration: '31 days',
			participants: 87,
			maxParticipants: 100,
			startDate: new Date(2024, 11, 1),
			endDate: new Date(2024, 11, 31),
			status: 'active',
			prize: '$500 gym credit + trophy',
			rules: [
				'Must be a current Power House member',
				'Proper form verified by trainer',
				'Maximum 3 attempts per week',
				'Video evidence required for final lift'
			],
			leaderboard: [
				{
					rank: 1,
					name: 'Marcus Steel',
					score: '585 lbs',
					avatar:
						'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=100&q=80'
				},
				{
					rank: 2,
					name: 'Sarah Kim',
					score: '405 lbs',
					avatar:
						'https://images.unsplash.com/photo-1494790108755-2616b612b34c?ixlib=rb-4.0.3&auto=format&fit=crop&w=100&q=80'
				},
				{
					rank: 3,
					name: 'Mike Rodriguez',
					score: '565 lbs',
					avatar:
						'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&auto=format&fit=crop&w=100&q=80'
				},
				{
					rank: 4,
					name: 'Lisa Chen',
					score: '315 lbs',
					avatar:
						'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&auto=format&fit=crop&w=100&q=80'
				},
				{
					rank: 5,
					name: 'James Wilson',
					score: '525 lbs',
					avatar:
						'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-4.0.3&auto=format&fit=crop&w=100&q=80'
				}
			]
		},
		{
			id: 'cardio-crusher',
			title: '30-Day Cardio Crusher',
			description: 'Accumulate 30 hours of cardio in 30 days. Track any cardio activity!',
			type: 'cardio',
			duration: '30 days',
			participants: 156,
			startDate: new Date(2024, 11, 1),
			endDate: new Date(2024, 11, 30),
			status: 'active',
			prize: 'Fitness tracker + supplements',
			rules: [
				'Any cardio activity counts (running, cycling, rowing, etc.)',
				'Minimum 20 minutes per session',
				'Heart rate must average 70%+ max HR',
				'Log activities in Power House app'
			],
			progress: { current: 18.5, target: 30, unit: 'hours' }
		},
		{
			id: 'team-transformation',
			title: 'Team Transformation Challenge',
			description: 'Form teams of 4 and compete for the best overall fitness improvement!',
			type: 'team',
			duration: '8 weeks',
			participants: 64,
			maxParticipants: 80,
			startDate: new Date(2024, 10, 15),
			endDate: new Date(2025, 0, 10),
			status: 'active',
			prize: '$2000 team prize + individual awards',
			rules: [
				'Teams must have exactly 4 members',
				'Weekly weigh-ins and measurements',
				'At least 3 workouts per week per person',
				'Team support and accountability required'
			]
		},
		{
			id: 'consistency-king',
			title: 'Consistency King/Queen',
			description: 'Most consistent member wins! Track daily habits and workout frequency.',
			type: 'consistency',
			duration: '90 days',
			participants: 203,
			startDate: new Date(2024, 10, 1),
			endDate: new Date(2025, 0, 30),
			status: 'active',
			prize: '6 months free membership',
			rules: [
				'Points for daily workouts, nutrition logging, sleep tracking',
				'Bonus points for helping other members',
				'Must maintain 80%+ consistency to qualify',
				'Weekly check-ins with accountability partner'
			],
			progress: { current: 67, target: 90, unit: 'days' }
		},
		{
			id: 'hiit-hero',
			title: 'HIIT Hero Challenge',
			description: 'Complete 50 HIIT sessions in 10 weeks. Build endurance and strength!',
			type: 'cardio',
			duration: '10 weeks',
			participants: 45,
			maxParticipants: 60,
			startDate: new Date(2025, 0, 15),
			endDate: new Date(2025, 2, 26),
			status: 'upcoming',
			prize: 'Personal training package',
			rules: [
				'HIIT sessions must be 20+ minutes',
				'Instructor-led classes preferred',
				'Self-guided sessions need approval',
				'Track heart rate and intensity'
			]
		}
	];

	const challengeTypes = {
		strength: { icon: '💪', color: 'bg-red-500', name: 'Strength' },
		cardio: { icon: '🔥', color: 'bg-orange-500', name: 'Cardio' },
		consistency: { icon: '⭐', color: 'bg-yellow-500', name: 'Consistency' },
		team: { icon: '👥', color: 'bg-blue-500', name: 'Team' }
	};

	const statusColors = {
		upcoming: 'text-blue-400 bg-blue-500/20',
		active: 'text-green-400 bg-green-500/20',
		completed: 'text-gray-400 bg-gray-500/20'
	};

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function getFilteredChallenges() {
		switch (selectedChallenge) {
			case 'current':
				return challenges.filter((c) => c.status === 'active');
			case 'upcoming':
				return challenges.filter((c) => c.status === 'upcoming');
			case 'completed':
				return challenges.filter((c) => c.status === 'completed');
			default:
				return challenges;
		}
	}

	$: filteredChallenges = getFilteredChallenges();
</script>

<section id="challenges" class="bg-black py-24">
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
				<span class="text-sm font-medium text-white/70">🏆 Push Your Limits</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				FITNESS
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					CHALLENGES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Push yourself beyond your comfort zone with our community challenges. Compete, improve, and
				achieve goals you never thought possible!
			</p>
		</div>

		<!-- Challenge Filter -->
		<div
			class="mb-12 flex transform justify-center transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="flex space-x-2 rounded-2xl border border-white/10 bg-white/5 p-2 backdrop-blur-md"
			>
				{#each [{ id: 'current', name: 'Active Now' }, { id: 'upcoming', name: 'Coming Soon' }, { id: 'all', name: 'All Challenges' }] as filter}
					<button
						on:click={() => (selectedChallenge = filter.id)}
						class="rounded-xl px-4 py-2 text-sm font-semibold transition-all duration-300 {selectedChallenge ===
						filter.id
							? 'bg-white text-black shadow-lg'
							: 'text-white hover:bg-white/10'}"
					>
						{filter.name}
					</button>
				{/each}
			</div>
		</div>

		<!-- Challenges Grid -->
		<div
			class="grid transform grid-cols-1 gap-8 transition-all delay-600 duration-1000 lg:grid-cols-2 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each filteredChallenges as challenge, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10"
					style="transition-delay: {index * 150}ms"
				>
					<!-- Challenge Header -->
					<div class="p-6 pb-4">
						<div class="mb-4 flex items-start justify-between">
							<div class="flex items-center space-x-3">
								<div
									class="flex h-12 w-12 items-center justify-center rounded-xl {challengeTypes[
										challenge.type
									].color}"
								>
									<span class="text-xl">{challengeTypes[challenge.type].icon}</span>
								</div>
								<div>
									<h3
										class="text-xl font-bold text-white transition-colors group-hover:text-gray-200"
									>
										{challenge.title}
									</h3>
									<p class="text-sm text-gray-400">{challenge.duration}</p>
								</div>
							</div>
							<div class="flex flex-col items-end space-y-2">
								<span
									class="rounded-full px-3 py-1 text-xs font-medium {statusColors[
										challenge.status
									]}"
								>
									{challenge.status.charAt(0).toUpperCase() + challenge.status.slice(1)}
								</span>
								<span class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white">
									{challengeTypes[challenge.type].name}
								</span>
							</div>
						</div>

						<!-- Description -->
						<p class="mb-4 leading-relaxed text-gray-300">
							{challenge.description}
						</p>

						<!-- Participants -->
						<div class="mb-4 flex items-center justify-between">
							<div class="flex items-center space-x-2">
								<svg
									class="h-4 w-4 text-white/70"
									fill="none"
									stroke="currentColor"
									viewBox="0 0 24 24"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										stroke-width="2"
										d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 715.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 919.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"
									/>
								</svg>
								<span class="text-gray-300">{challenge.participants} participants</span>
							</div>
							{#if challenge.maxParticipants}
								<span class="text-sm text-gray-400">
									{challenge.maxParticipants - challenge.participants} spots left
								</span>
							{/if}
						</div>

						<!-- Progress Bar (if applicable) -->
						{#if challenge.progress}
							<div class="mb-4">
								<div class="mb-1 flex justify-between text-sm">
									<span class="text-gray-400">Progress</span>
									<span class="text-white">
										{challenge.progress.current}/{challenge.progress.target}
										{challenge.progress.unit}
									</span>
								</div>
								<div class="h-2 rounded-full bg-white/20">
									<div
										class="h-2 rounded-full bg-gradient-to-r from-green-400 to-green-300 transition-all duration-500"
										style="width: {(challenge.progress.current / challenge.progress.target) * 100}%"
									></div>
								</div>
							</div>
						{/if}

						<!-- Prize -->
						<div class="mb-4 rounded-xl border border-yellow-500/20 bg-yellow-500/10 p-3">
							<div class="flex items-center space-x-2">
								<svg class="h-4 w-4 text-yellow-400" fill="currentColor" viewBox="0 0 24 24">
									<path
										d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
									/>
								</svg>
								<span class="text-sm font-medium text-yellow-400">Prize: {challenge.prize}</span>
							</div>
						</div>
					</div>

					<!-- Leaderboard (if available) -->
					{#if challenge.leaderboard}
						<div class="border-t border-white/10 p-6 pt-4">
							<h4 class="mb-3 text-lg font-semibold text-white">Current Leaderboard</h4>
							<div class="space-y-2">
								{#each challenge.leaderboard.slice(0, 3) as leader}
									<div class="flex items-center justify-between rounded-lg bg-white/5 p-2">
										<div class="flex items-center space-x-3">
											<span
												class="flex h-6 w-6 items-center justify-center rounded-full bg-white/20 text-xs font-bold text-white"
											>
												{leader.rank}
											</span>
											<img
												src={leader.avatar}
												alt={leader.name}
												class="h-8 w-8 rounded-full object-cover"
											/>
											<span class="text-white">{leader.name}</span>
										</div>
										<span class="font-bold text-white">{leader.score}</span>
									</div>
								{/each}
							</div>
						</div>
					{/if}

					<!-- Rules -->
					<div class="border-t border-white/10 p-6 pt-4">
						<h4 class="mb-3 text-lg font-semibold text-white">Rules</h4>
						<ul class="space-y-1">
							{#each challenge.rules.slice(0, 3) as rule}
								<li class="flex items-start space-x-2">
									<div class="mt-2 h-1 w-1 rounded-full bg-white/60"></div>
									<span class="text-sm text-gray-300">{rule}</span>
								</li>
							{/each}
						</ul>
					</div>

					<!-- Action Button -->
					<div class="p-6 pt-4">
						<button
							class="w-full rounded-xl bg-white px-4 py-3 text-sm font-bold text-black transition-colors duration-300 hover:bg-gray-200 disabled:cursor-not-allowed disabled:opacity-50"
							disabled={challenge.status === 'completed' ||
								(challenge.maxParticipants && challenge.participants >= challenge.maxParticipants)}
						>
							{#if challenge.status === 'completed'}
								Challenge Completed
							{:else if challenge.maxParticipants && challenge.participants >= challenge.maxParticipants}
								Challenge Full
							{:else if challenge.status === 'upcoming'}
								Pre-Register
							{:else}
								Join Challenge
							{/if}
						</button>
					</div>
				</div>
			{/each}
		</div>

		<!-- Challenge Stats -->
		<div
			class="mt-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="grid grid-cols-1 gap-6 md:grid-cols-4">
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md">
					<div class="mb-2 text-3xl font-black text-white">50+</div>
					<div class="text-sm text-gray-400">Active Challenges</div>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md">
					<div class="mb-2 text-3xl font-black text-white">1200+</div>
					<div class="text-sm text-gray-400">Total Participants</div>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md">
					<div class="mb-2 text-3xl font-black text-white">$25K+</div>
					<div class="text-sm text-gray-400">Prizes Awarded</div>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md">
					<div class="mb-2 text-3xl font-black text-white">95%</div>
					<div class="text-sm text-gray-400">Completion Rate</div>
				</div>
			</div>
		</div>

		<!-- Create Challenge CTA -->
		<div
			class="mt-16 transform text-center transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-2xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md"
			>
				<h4 class="mb-4 text-2xl font-bold text-white">Ready to Challenge Yourself?</h4>
				<p class="mb-6 text-gray-300">
					Join our community challenges and discover what you're truly capable of. Compete, improve,
					and win amazing prizes!
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Browse All Challenges
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Suggest Challenge
					</button>
				</div>
			</div>
		</div>
	</div>
</section>
