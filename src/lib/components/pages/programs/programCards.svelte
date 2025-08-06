<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let activeFilter = 'all';

	interface Program {
		id: string;
		name: string;
		category: string;
		description: string;
		duration: string;
		intensity: string;
		image: string;
		trainer: string;
		schedule: string[];
		features: string[];
		difficulty: 'Beginner' | 'Intermediate' | 'Advanced';
		maxParticipants: number;
	}

	const programs: Program[] = [
		{
			id: 'beast-mode',
			name: 'Beast Mode',
			category: 'strength',
			description:
				'Ultimate strength and power training program designed for serious athletes looking to push their limits.',
			duration: '60 min',
			intensity: 'High',
			image:
				'https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			trainer: 'Marcus Steel',
			schedule: ['Mon 6:00 AM', 'Wed 7:00 PM', 'Fri 6:00 AM'],
			features: ['Heavy Lifting', 'Compound Movements', 'Progressive Overload', 'Strength Focus'],
			difficulty: 'Advanced',
			maxParticipants: 12
		},
		{
			id: 'cardio-blast',
			name: 'Cardio Blast',
			category: 'cardio',
			description:
				'High-energy cardiovascular training that burns calories and builds endurance through varied cardio exercises.',
			duration: '45 min',
			intensity: 'High',
			image:
				'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			trainer: 'Sarah Johnson',
			schedule: ['Tue 6:30 AM', 'Thu 6:00 PM', 'Sat 9:00 AM'],
			features: ['Fat Burning', 'Heart Health', 'Endurance', 'High Energy'],
			difficulty: 'Intermediate',
			maxParticipants: 20
		},
		{
			id: 'hiit-warrior',
			name: 'HIIT Warrior',
			category: 'hiit',
			description:
				'Intense interval training combining strength and cardio for maximum calorie burn and fitness gains.',
			duration: '30 min',
			intensity: 'Very High',
			image:
				'https://images.unsplash.com/photo-1534438327276-14e5300c3a48?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			trainer: 'Alex Chen',
			schedule: ['Mon 12:00 PM', 'Wed 6:00 PM', 'Fri 12:00 PM'],
			features: ['HIIT Training', 'Full Body', 'Time Efficient', 'Metabolic Boost'],
			difficulty: 'Advanced',
			maxParticipants: 15
		},
		{
			id: 'power-lifting',
			name: 'Power Lifting',
			category: 'strength',
			description:
				'Focus on the big three: squat, bench press, and deadlift. Perfect technique and progressive strength building.',
			duration: '75 min',
			intensity: 'High',
			image:
				'https://images.unsplash.com/photo-1583500178690-f7eb6bdecf5c?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			trainer: 'Mike Rodriguez',
			schedule: ['Tue 7:00 AM', 'Thu 7:00 AM', 'Sat 10:00 AM'],
			features: ['Powerlifting Technique', 'Strength Building', 'Competition Prep', 'Form Focus'],
			difficulty: 'Advanced',
			maxParticipants: 10
		},
		{
			id: 'yoga-flow',
			name: 'Yoga Flow',
			category: 'recovery',
			description:
				'Dynamic yoga sequences to improve flexibility, balance, and mental clarity while promoting recovery.',
			duration: '60 min',
			intensity: 'Low',
			image:
				'https://images.unsplash.com/photo-1506629905607-c7a4e6d05e4c?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			trainer: 'Emma Wilson',
			schedule: ['Mon 7:00 PM', 'Wed 9:00 AM', 'Sun 10:00 AM'],
			features: ['Flexibility', 'Balance', 'Stress Relief', 'Mind-Body'],
			difficulty: 'Beginner',
			maxParticipants: 25
		},
		{
			id: 'functional-fitness',
			name: 'Functional Fitness',
			category: 'hiit',
			description:
				'Real-world movement patterns that improve daily life performance and overall functional strength.',
			duration: '50 min',
			intensity: 'Medium',
			image:
				'https://images.unsplash.com/photo-1549060279-7e168fcee0c2?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			trainer: 'David Kim',
			schedule: ['Tue 5:30 PM', 'Thu 12:00 PM', 'Sat 8:00 AM'],
			features: ['Functional Movement', 'Core Stability', 'Balance', 'Practical Strength'],
			difficulty: 'Intermediate',
			maxParticipants: 18
		}
	];

	let filteredPrograms = programs;

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);

		// Listen for filter changes
		const handleFilterChange = (event: CustomEvent) => {
			activeFilter = event.detail;
			filterPrograms();
		};

		window.addEventListener('programFilterChange', handleFilterChange as EventListener);

		return () => {
			window.removeEventListener('programFilterChange', handleFilterChange as EventListener);
		};
	});

	function filterPrograms() {
		if (activeFilter === 'all') {
			filteredPrograms = programs;
		} else {
			filteredPrograms = programs.filter((program) => program.category === activeFilter);
		}
	}

	function getIntensityColor(intensity: string) {
		switch (intensity) {
			case 'Low':
				return 'bg-green-500';
			case 'Medium':
				return 'bg-yellow-500';
			case 'High':
				return 'bg-orange-500';
			case 'Very High':
				return 'bg-red-500';
			default:
				return 'bg-gray-500';
		}
	}

	function getDifficultyColor(difficulty: string) {
		switch (difficulty) {
			case 'Beginner':
				return 'text-green-400';
			case 'Intermediate':
				return 'text-yellow-400';
			case 'Advanced':
				return 'text-red-400';
			default:
				return 'text-gray-400';
		}
	}
</script>

<section class="bg-black py-24">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<!-- Programs Grid -->
		<div
			class="grid transform grid-cols-1 gap-8 transition-all delay-200 duration-1000 md:grid-cols-2 lg:grid-cols-3 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each filteredPrograms as program, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md transition-all duration-500 hover:scale-105 hover:border-white/20 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<!-- Program Image -->
					<div class="relative h-64 overflow-hidden">
						<img
							src={program.image}
							alt={program.name}
							class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
						/>
						<div class="absolute inset-0 bg-black/40"></div>

						<!-- Intensity Badge -->
						<div class="absolute top-4 left-4">
							<div
								class="flex items-center space-x-2 rounded-full bg-black/60 px-3 py-1 backdrop-blur-md"
							>
								<div class="h-2 w-2 rounded-full {getIntensityColor(program.intensity)}"></div>
								<span class="text-xs font-medium text-white">{program.intensity} Intensity</span>
							</div>
						</div>

						<!-- Duration -->
						<div class="absolute top-4 right-4">
							<div class="rounded-full bg-white/20 px-3 py-1 backdrop-blur-md">
								<span class="text-xs font-medium text-white">{program.duration}</span>
							</div>
						</div>

						<!-- Difficulty -->
						<div class="absolute bottom-4 left-4">
							<span class="text-sm font-bold {getDifficultyColor(program.difficulty)}">
								{program.difficulty}
							</span>
						</div>
					</div>

					<!-- Program Info -->
					<div class="p-6">
						<!-- Program Name -->
						<h3
							class="mb-3 text-2xl font-bold text-white transition-colors group-hover:text-gray-200"
						>
							{program.name}
						</h3>

						<!-- Description -->
						<p class="mb-4 leading-relaxed text-gray-300">
							{program.description}
						</p>

						<!-- Features -->
						<div class="mb-6 flex flex-wrap gap-2">
							{#each program.features.slice(0, 3) as feature}
								<span class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white/80">
									{feature}
								</span>
							{/each}
							{#if program.features.length > 3}
								<span class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white/60">
									+{program.features.length - 3} more
								</span>
							{/if}
						</div>

						<!-- Trainer & Schedule Info -->
						<div class="mb-6 space-y-3">
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
										d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"
									/>
								</svg>
								<span class="text-sm text-gray-300">Trainer: {program.trainer}</span>
							</div>
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
								<span class="text-sm text-gray-300">Max {program.maxParticipants} participants</span
								>
							</div>
						</div>

						<!-- Schedule -->
						<div class="mb-6">
							<h4 class="mb-2 text-sm font-semibold text-white">This Week's Schedule:</h4>
							<div class="space-y-1">
								{#each program.schedule as time}
									<div class="flex items-center justify-between rounded-lg bg-white/5 px-3 py-1">
										<span class="text-sm text-gray-300">{time}</span>
										<span class="text-xs text-green-400">Available</span>
									</div>
								{/each}
							</div>
						</div>

						<!-- CTA Buttons -->
						<div class="flex space-x-3">
							<button
								class="flex-1 rounded-xl bg-white px-4 py-3 text-sm font-bold text-black transition-colors duration-300 hover:bg-gray-200"
							>
								Book Class
							</button>
							<button
								class="rounded-xl border border-white/20 bg-white/10 px-4 py-3 text-sm font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
							>
								Learn More
							</button>
						</div>
					</div>

					<!-- Hover Overlay -->
					<div
						class="absolute inset-0 opacity-0 transition-opacity duration-300 group-hover:opacity-100"
					>
						<div
							class="absolute inset-0 bg-gradient-to-t from-black/20 via-transparent to-transparent"
						></div>
					</div>
				</div>
			{/each}
		</div>

		<!-- Empty State -->
		{#if filteredPrograms.length === 0}
			<div class="py-24 text-center">
				<div class="mb-4 text-6xl">🏃‍♂️</div>
				<h3 class="mb-2 text-2xl font-bold text-white">No programs found</h3>
				<p class="text-gray-400">Try selecting a different category filter.</p>
			</div>
		{/if}

		<!-- Programs Info -->
		<div
			class="mt-16 transform text-center transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="inline-flex items-center space-x-6 rounded-2xl border border-white/10 bg-white/5 px-8 py-4 backdrop-blur-md"
			>
				<div class="text-center">
					<div class="text-2xl font-bold text-white">{filteredPrograms.length}</div>
					<div class="text-xs text-gray-400">Programs Available</div>
				</div>
				<div class="h-8 w-px bg-white/20"></div>
				<div class="text-center">
					<div class="text-2xl font-bold text-white">50+</div>
					<div class="text-xs text-gray-400">Classes This Week</div>
				</div>
				<div class="h-8 w-px bg-white/20"></div>
				<div class="text-center">
					<div class="text-2xl font-bold text-white">Free</div>
					<div class="text-xs text-gray-400">Trial Class</div>
				</div>
			</div>
		</div>
	</div>
</section>
