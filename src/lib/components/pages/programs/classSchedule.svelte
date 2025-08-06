<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let selectedDay = 'monday';

	interface ClassSession {
		time: string;
		program: string;
		trainer: string;
		duration: string;
		capacity: number;
		booked: number;
		difficulty: 'Beginner' | 'Intermediate' | 'Advanced';
		room: string;
	}

	const schedule: Record<string, ClassSession[]> = {
		monday: [
			{
				time: '06:00',
				program: 'Beast Mode',
				trainer: 'Marcus Steel',
				duration: '60 min',
				capacity: 12,
				booked: 8,
				difficulty: 'Advanced',
				room: 'Studio A'
			},
			{
				time: '07:30',
				program: 'Yoga Flow',
				trainer: 'Emma Wilson',
				duration: '60 min',
				capacity: 25,
				booked: 18,
				difficulty: 'Beginner',
				room: 'Studio B'
			},
			{
				time: '12:00',
				program: 'HIIT Warrior',
				trainer: 'Alex Chen',
				duration: '30 min',
				capacity: 15,
				booked: 12,
				difficulty: 'Advanced',
				room: 'Studio A'
			},
			{
				time: '17:30',
				program: 'Functional Fitness',
				trainer: 'David Kim',
				duration: '50 min',
				capacity: 18,
				booked: 14,
				difficulty: 'Intermediate',
				room: 'Studio C'
			},
			{
				time: '19:00',
				program: 'Yoga Flow',
				trainer: 'Emma Wilson',
				duration: '60 min',
				capacity: 25,
				booked: 22,
				difficulty: 'Beginner',
				room: 'Studio B'
			}
		],
		tuesday: [
			{
				time: '06:30',
				program: 'Cardio Blast',
				trainer: 'Sarah Johnson',
				duration: '45 min',
				capacity: 20,
				booked: 16,
				difficulty: 'Intermediate',
				room: 'Studio A'
			},
			{
				time: '07:00',
				program: 'Power Lifting',
				trainer: 'Mike Rodriguez',
				duration: '75 min',
				capacity: 10,
				booked: 8,
				difficulty: 'Advanced',
				room: 'Weight Room'
			},
			{
				time: '12:30',
				program: 'Functional Fitness',
				trainer: 'David Kim',
				duration: '50 min',
				capacity: 18,
				booked: 11,
				difficulty: 'Intermediate',
				room: 'Studio C'
			},
			{
				time: '17:30',
				program: 'Functional Fitness',
				trainer: 'David Kim',
				duration: '50 min',
				capacity: 18,
				booked: 15,
				difficulty: 'Intermediate',
				room: 'Studio C'
			},
			{
				time: '18:30',
				program: 'Beast Mode',
				trainer: 'Marcus Steel',
				duration: '60 min',
				capacity: 12,
				booked: 10,
				difficulty: 'Advanced',
				room: 'Studio A'
			}
		],
		wednesday: [
			{
				time: '06:00',
				program: 'Beast Mode',
				trainer: 'Marcus Steel',
				duration: '60 min',
				capacity: 12,
				booked: 9,
				difficulty: 'Advanced',
				room: 'Studio A'
			},
			{
				time: '09:00',
				program: 'Yoga Flow',
				trainer: 'Emma Wilson',
				duration: '60 min',
				capacity: 25,
				booked: 15,
				difficulty: 'Beginner',
				room: 'Studio B'
			},
			{
				time: '12:00',
				program: 'HIIT Warrior',
				trainer: 'Alex Chen',
				duration: '30 min',
				capacity: 15,
				booked: 13,
				difficulty: 'Advanced',
				room: 'Studio A'
			},
			{
				time: '18:00',
				program: 'HIIT Warrior',
				trainer: 'Alex Chen',
				duration: '30 min',
				capacity: 15,
				booked: 14,
				difficulty: 'Advanced',
				room: 'Studio A'
			},
			{
				time: '19:30',
				program: 'Cardio Blast',
				trainer: 'Sarah Johnson',
				duration: '45 min',
				capacity: 20,
				booked: 17,
				difficulty: 'Intermediate',
				room: 'Studio C'
			}
		],
		thursday: [
			{
				time: '07:00',
				program: 'Power Lifting',
				trainer: 'Mike Rodriguez',
				duration: '75 min',
				capacity: 10,
				booked: 7,
				difficulty: 'Advanced',
				room: 'Weight Room'
			},
			{
				time: '12:00',
				program: 'Functional Fitness',
				trainer: 'David Kim',
				duration: '50 min',
				capacity: 18,
				booked: 12,
				difficulty: 'Intermediate',
				room: 'Studio C'
			},
			{
				time: '18:00',
				program: 'Cardio Blast',
				trainer: 'Sarah Johnson',
				duration: '45 min',
				capacity: 20,
				booked: 18,
				difficulty: 'Intermediate',
				room: 'Studio A'
			},
			{
				time: '19:15',
				program: 'Beast Mode',
				trainer: 'Marcus Steel',
				duration: '60 min',
				capacity: 12,
				booked: 11,
				difficulty: 'Advanced',
				room: 'Studio A'
			}
		],
		friday: [
			{
				time: '06:00',
				program: 'Beast Mode',
				trainer: 'Marcus Steel',
				duration: '60 min',
				capacity: 12,
				booked: 10,
				difficulty: 'Advanced',
				room: 'Studio A'
			},
			{
				time: '12:00',
				program: 'HIIT Warrior',
				trainer: 'Alex Chen',
				duration: '30 min',
				capacity: 15,
				booked: 11,
				difficulty: 'Advanced',
				room: 'Studio A'
			},
			{
				time: '17:00',
				program: 'Functional Fitness',
				trainer: 'David Kim',
				duration: '50 min',
				capacity: 18,
				booked: 13,
				difficulty: 'Intermediate',
				room: 'Studio C'
			},
			{
				time: '18:30',
				program: 'Cardio Blast',
				trainer: 'Sarah Johnson',
				duration: '45 min',
				capacity: 20,
				booked: 19,
				difficulty: 'Intermediate',
				room: 'Studio C'
			}
		],
		saturday: [
			{
				time: '08:00',
				program: 'Functional Fitness',
				trainer: 'David Kim',
				duration: '50 min',
				capacity: 18,
				booked: 14,
				difficulty: 'Intermediate',
				room: 'Studio C'
			},
			{
				time: '09:00',
				program: 'Cardio Blast',
				trainer: 'Sarah Johnson',
				duration: '45 min',
				capacity: 20,
				booked: 16,
				difficulty: 'Intermediate',
				room: 'Studio A'
			},
			{
				time: '10:00',
				program: 'Power Lifting',
				trainer: 'Mike Rodriguez',
				duration: '75 min',
				capacity: 10,
				booked: 8,
				difficulty: 'Advanced',
				room: 'Weight Room'
			},
			{
				time: '11:30',
				program: 'Beast Mode',
				trainer: 'Marcus Steel',
				duration: '60 min',
				capacity: 12,
				booked: 9,
				difficulty: 'Advanced',
				room: 'Studio A'
			}
		],
		sunday: [
			{
				time: '09:00',
				program: 'Yoga Flow',
				trainer: 'Emma Wilson',
				duration: '60 min',
				capacity: 25,
				booked: 20,
				difficulty: 'Beginner',
				room: 'Studio B'
			},
			{
				time: '10:30',
				program: 'Yoga Flow',
				trainer: 'Emma Wilson',
				duration: '60 min',
				capacity: 25,
				booked: 17,
				difficulty: 'Beginner',
				room: 'Studio B'
			},
			{
				time: '16:00',
				program: 'Functional Fitness',
				trainer: 'David Kim',
				duration: '50 min',
				capacity: 18,
				booked: 10,
				difficulty: 'Intermediate',
				room: 'Studio C'
			}
		]
	};

	const days = [
		{ id: 'monday', name: 'Monday', short: 'Mon' },
		{ id: 'tuesday', name: 'Tuesday', short: 'Tue' },
		{ id: 'wednesday', name: 'Wednesday', short: 'Wed' },
		{ id: 'thursday', name: 'Thursday', short: 'Thu' },
		{ id: 'friday', name: 'Friday', short: 'Fri' },
		{ id: 'saturday', name: 'Saturday', short: 'Sat' },
		{ id: 'sunday', name: 'Sunday', short: 'Sun' }
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);

		// Set current day as default
		const today = new Date().toLocaleLowerCase();
		const dayNames = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];
		selectedDay = dayNames[new Date().getDay()];
	});

	function getDifficultyColor(difficulty: string) {
		switch (difficulty) {
			case 'Beginner':
				return 'text-green-400 bg-green-500/20';
			case 'Intermediate':
				return 'text-yellow-400 bg-yellow-500/20';
			case 'Advanced':
				return 'text-red-400 bg-red-500/20';
			default:
				return 'text-gray-400 bg-gray-500/20';
		}
	}

	function getAvailabilityStatus(booked: number, capacity: number) {
		const percentage = (booked / capacity) * 100;
		if (percentage >= 100) return { text: 'Full', color: 'text-red-400 bg-red-500/20' };
		if (percentage >= 80) return { text: 'Almost Full', color: 'text-orange-400 bg-orange-500/20' };
		if (percentage >= 50) return { text: 'Available', color: 'text-yellow-400 bg-yellow-500/20' };
		return { text: 'Open', color: 'text-green-400 bg-green-500/20' };
	}
</script>

<section class="bg-black py-24">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<!-- Section Header -->
		<div
			class="mb-16 transform text-center transition-all delay-200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mb-6 inline-flex items-center rounded-full border border-white/10 bg-white/5 px-6 py-2"
			>
				<span class="text-sm font-medium text-white/70">📅 Weekly Schedule</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				CLASS
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					SCHEDULE
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Plan your week with our comprehensive class schedule. Book your spot and never miss a
				workout.
			</p>
		</div>

		<!-- Day Selector -->
		<div
			class="mb-12 flex transform justify-center transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="flex space-x-2 rounded-2xl border border-white/10 bg-white/5 p-2 backdrop-blur-md"
			>
				{#each days as day}
					<button
						on:click={() => (selectedDay = day.id)}
						class="rounded-xl px-4 py-2 text-sm font-semibold transition-all duration-300 {selectedDay ===
						day.id
							? 'bg-white text-black shadow-lg'
							: 'text-white hover:bg-white/10'}"
					>
						<span class="hidden sm:inline">{day.name}</span>
						<span class="sm:hidden">{day.short}</span>
					</button>
				{/each}
			</div>
		</div>

		<!-- Schedule Grid -->
		<div
			class="transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#if schedule[selectedDay] && schedule[selectedDay].length > 0}
				<div class="space-y-4">
					{#each schedule[selectedDay] as session, index}
						<div
							class="group rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md transition-all duration-300 hover:border-white/20 hover:bg-white/10"
							style="transition-delay: {index * 100}ms"
						>
							<div
								class="flex flex-col space-y-4 lg:flex-row lg:items-center lg:justify-between lg:space-y-0"
							>
								<!-- Time & Program Info -->
								<div
									class="flex flex-col space-y-2 lg:flex-row lg:items-center lg:space-y-0 lg:space-x-6"
								>
									<!-- Time -->
									<div class="text-center lg:text-left">
										<div class="text-3xl font-black text-white">{session.time}</div>
										<div class="text-sm text-gray-400">{session.duration}</div>
									</div>

									<!-- Program Details -->
									<div class="flex-1">
										<h3
											class="mb-2 text-xl font-bold text-white transition-colors group-hover:text-gray-200"
										>
											{session.program}
										</h3>
										<div class="flex flex-wrap items-center gap-3">
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
												<span class="text-sm text-gray-300">{session.trainer}</span>
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
														d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"
													/>
												</svg>
												<span class="text-sm text-gray-300">{session.room}</span>
											</div>
										</div>
									</div>
								</div>

								<!-- Badges & Booking -->
								<div class="flex flex-col space-y-3 lg:items-end">
									<!-- Badges -->
									<div class="flex flex-wrap gap-2">
										<span
											class="rounded-full px-3 py-1 text-xs font-medium {getDifficultyColor(
												session.difficulty
											)}"
										>
											{session.difficulty}
										</span>
										<span
											class="rounded-full px-3 py-1 text-xs font-medium {getAvailabilityStatus(
												session.booked,
												session.capacity
											).color}"
										>
											{getAvailabilityStatus(session.booked, session.capacity).text}
										</span>
									</div>

									<!-- Capacity Info -->
									<div class="text-center lg:text-right">
										<div class="text-sm text-gray-300">
											{session.booked}/{session.capacity} booked
										</div>
										<div class="mt-1 h-2 w-32 rounded-full bg-white/20">
											<div
												class="h-2 rounded-full bg-gradient-to-r from-white to-gray-300 transition-all duration-500"
												style="width: {(session.booked / session.capacity) * 100}%"
											></div>
										</div>
									</div>

									<!-- Book Button -->
									<button
										class="rounded-xl bg-white px-6 py-2 text-sm font-bold text-black transition-all duration-300 hover:bg-gray-200 disabled:cursor-not-allowed disabled:opacity-50"
										disabled={session.booked >= session.capacity}
									>
										{session.booked >= session.capacity ? 'Full' : 'Book Now'}
									</button>
								</div>
							</div>
						</div>
					{/each}
				</div>
			{:else}
				<div class="py-16 text-center">
					<div class="mb-4 text-6xl">🏃‍♂️</div>
					<h3 class="mb-2 text-2xl font-bold text-white">No classes scheduled</h3>
					<p class="text-gray-400">Check back soon or try another day.</p>
				</div>
			{/if}
		</div>

		<!-- Schedule Info -->
		<div
			class="mt-16 transform text-center transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="inline-flex flex-col space-y-4 rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md sm:flex-row sm:items-center sm:space-y-0 sm:space-x-8"
			>
				<div class="flex items-center space-x-2">
					<svg class="h-5 w-5 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
						/>
					</svg>
					<span class="text-sm font-medium text-white"
						>Free cancellation up to 2 hours before class</span
					>
				</div>
				<div class="flex items-center space-x-2">
					<svg class="h-5 w-5 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
						/>
					</svg>
					<span class="text-sm font-medium text-white"
						>Classes start promptly at scheduled time</span
					>
				</div>
				<div class="flex items-center space-x-2">
					<svg
						class="h-5 w-5 text-yellow-400"
						fill="none"
						stroke="currentColor"
						viewBox="0 0 24 24"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
						/>
					</svg>
					<span class="text-sm font-medium text-white">Bring water bottle and towel</span>
				</div>
			</div>
		</div>
	</div>
</section>
