<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let selectedDate = new Date();
	let currentMonth = new Date().getMonth();
	let currentYear = new Date().getFullYear();

	interface CommunityEvent {
		id: string;
		title: string;
		date: Date;
		time: string;
		duration: string;
		type: 'workout' | 'social' | 'challenge' | 'workshop';
		description: string;
		capacity: number;
		registered: number;
		location: string;
		organizer: string;
	}

	const eventTypes = {
		workout: { icon: '💪', color: 'bg-red-500', name: 'Workout' },
		social: { icon: '🎉', color: 'bg-blue-500', name: 'Social' },
		challenge: { icon: '🏆', color: 'bg-yellow-500', name: 'Challenge' },
		workshop: { icon: '📚', color: 'bg-green-500', name: 'Workshop' }
	};

	const upcomingEvents: CommunityEvent[] = [
		{
			id: 'group-hiit-1',
			title: 'Community HIIT Challenge',
			date: new Date(2024, 11, 15),
			time: '6:00 PM',
			duration: '45 min',
			type: 'workout',
			description: 'High-intensity group workout with prizes for participation!',
			capacity: 30,
			registered: 24,
			location: 'Main Studio',
			organizer: 'Sarah Johnson'
		},
		{
			id: 'nutrition-workshop',
			title: 'Nutrition Workshop: Meal Prep Mastery',
			date: new Date(2024, 11, 18),
			time: '10:00 AM',
			duration: '2 hours',
			type: 'workshop',
			description:
				'Learn meal prep strategies for busy lifestyles. Hands-on cooking session included!',
			capacity: 20,
			registered: 16,
			location: 'Classroom',
			organizer: 'Lisa Park'
		},
		{
			id: 'member-mixer',
			title: 'Monthly Member Mixer',
			date: new Date(2024, 11, 20),
			time: '7:00 PM',
			duration: '2 hours',
			type: 'social',
			description: 'Connect with fellow members over healthy snacks and fun activities!',
			capacity: 50,
			registered: 35,
			location: 'Lounge Area',
			organizer: 'Community Team'
		},
		{
			id: 'deadlift-challenge',
			title: 'December Deadlift Challenge',
			date: new Date(2024, 11, 22),
			time: '8:00 AM',
			duration: 'All day',
			type: 'challenge',
			description: 'Test your max deadlift! Multiple weight categories with prizes.',
			capacity: 40,
			registered: 28,
			location: 'Weight Room',
			organizer: 'Marcus Steel'
		},
		{
			id: 'yoga-flow',
			title: 'Sunrise Yoga Flow',
			date: new Date(2024, 11, 25),
			time: '6:30 AM',
			duration: '60 min',
			type: 'workout',
			description: 'Start your day with mindful movement and positive energy.',
			capacity: 25,
			registered: 18,
			location: 'Studio B',
			organizer: 'Emma Wilson'
		},
		{
			id: 'powerlifting-seminar',
			title: 'Powerlifting Technique Seminar',
			date: new Date(2024, 11, 28),
			time: '2:00 PM',
			duration: '3 hours',
			type: 'workshop',
			description: 'Master the big three lifts with professional coaching and video analysis.',
			capacity: 15,
			registered: 12,
			location: 'Weight Room',
			organizer: 'Mike Rodriguez'
		}
	];

	const monthNames = [
		'January',
		'February',
		'March',
		'April',
		'May',
		'June',
		'July',
		'August',
		'September',
		'October',
		'November',
		'December'
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function getEventsForDate(date: Date) {
		return upcomingEvents.filter(
			(event) =>
				event.date.getDate() === date.getDate() &&
				event.date.getMonth() === date.getMonth() &&
				event.date.getFullYear() === date.getFullYear()
		);
	}

	function isToday(date: Date) {
		const today = new Date();
		return (
			date.getDate() === today.getDate() &&
			date.getMonth() === today.getMonth() &&
			date.getFullYear() === today.getFullYear()
		);
	}

	function getDaysInMonth(month: number, year: number) {
		return new Date(year, month + 1, 0).getDate();
	}

	function getFirstDayOfMonth(month: number, year: number) {
		return new Date(year, month, 1).getDay();
	}
</script>

<section id="events" class="bg-black py-24">
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
				<span class="text-sm font-medium text-white/70">📅 What's Happening</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				COMMUNITY
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					EVENTS
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				From workout challenges to social mixers, there's always something exciting happening in our
				community. Join us and make new connections!
			</p>
		</div>

		<div class="grid grid-cols-1 gap-12 lg:grid-cols-2">
			<!-- Upcoming Events List -->
			<div
				class="transform transition-all delay-400 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<h3 class="mb-8 text-2xl font-bold text-white">Upcoming Events</h3>
				<div class="space-y-6">
					{#each upcomingEvents as event, index}
						<div
							class="group rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md transition-all duration-300 hover:border-white/20 hover:bg-white/10"
							style="transition-delay: {index * 100}ms"
						>
							<!-- Event Header -->
							<div class="mb-4 flex items-start justify-between">
								<div class="flex items-center space-x-3">
									<div
										class="flex h-12 w-12 items-center justify-center rounded-xl {eventTypes[
											event.type
										].color}"
									>
										<span class="text-xl">{eventTypes[event.type].icon}</span>
									</div>
									<div>
										<h4
											class="text-lg font-bold text-white transition-colors group-hover:text-gray-200"
										>
											{event.title}
										</h4>
										<p class="text-sm text-gray-400">by {event.organizer}</p>
									</div>
								</div>
								<span class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white">
									{eventTypes[event.type].name}
								</span>
							</div>

							<!-- Event Details -->
							<div class="mb-4 grid grid-cols-2 gap-4 text-sm">
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
											d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
										/>
									</svg>
									<span class="text-gray-300">{event.date.toLocaleDateString()}</span>
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
											d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
										/>
									</svg>
									<span class="text-gray-300">{event.time} ({event.duration})</span>
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
											d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
										/>
									</svg>
									<span class="text-gray-300">{event.location}</span>
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
									<span class="text-gray-300">{event.registered}/{event.capacity} registered</span>
								</div>
							</div>

							<!-- Description -->
							<p class="mb-4 text-gray-300">{event.description}</p>

							<!-- Capacity Bar -->
							<div class="mb-4">
								<div class="mb-1 flex justify-between text-sm">
									<span class="text-gray-400">Registration</span>
									<span class="text-white"
										>{Math.round((event.registered / event.capacity) * 100)}% full</span
									>
								</div>
								<div class="h-2 rounded-full bg-white/20">
									<div
										class="h-2 rounded-full bg-gradient-to-r from-white to-gray-300 transition-all duration-500"
										style="width: {(event.registered / event.capacity) * 100}%"
									></div>
								</div>
							</div>

							<!-- Action Button -->
							<button
								class="w-full rounded-xl bg-white px-4 py-3 text-sm font-bold text-black transition-colors duration-300 hover:bg-gray-200 disabled:cursor-not-allowed disabled:opacity-50"
								disabled={event.registered >= event.capacity}
							>
								{event.registered >= event.capacity ? 'Event Full' : 'Register Now'}
							</button>
						</div>
					{/each}
				</div>
			</div>

			<!-- Calendar View -->
			<div
				class="transform transition-all delay-600 duration-1000 {isVisible
					? 'translate-y-0 opacity-100'
					: 'translate-y-8 opacity-0'}"
			>
				<div class="rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<h3 class="mb-6 text-2xl font-bold text-white">Event Calendar</h3>

					<!-- Calendar Header -->
					<div class="mb-6 flex items-center justify-between">
						<h4 class="text-xl font-semibold text-white">
							{monthNames[currentMonth]}
							{currentYear}
						</h4>
						<div class="flex space-x-2">
							<button
								on:click={() => {
									if (currentMonth === 0) {
										currentMonth = 11;
										currentYear--;
									} else {
										currentMonth--;
									}
								}}
								class="rounded-lg bg-white/10 p-2 text-white transition-colors hover:bg-white/20"
							>
								<svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										stroke-width="2"
										d="M15 19l-7-7 7-7"
									/>
								</svg>
							</button>
							<button
								on:click={() => {
									if (currentMonth === 11) {
										currentMonth = 0;
										currentYear++;
									} else {
										currentMonth++;
									}
								}}
								class="rounded-lg bg-white/10 p-2 text-white transition-colors hover:bg-white/20"
							>
								<svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
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

					<!-- Calendar Grid -->
					<div class="grid grid-cols-7 gap-1">
						<!-- Day Headers -->
						{#each ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'] as day}
							<div class="p-2 text-center text-sm font-medium text-gray-400">
								{day}
							</div>
						{/each}

						<!-- Calendar Days -->
						{#each Array(getFirstDayOfMonth(currentMonth, currentYear)) as _}
							<div class="p-2"></div>
						{/each}

						{#each Array(getDaysInMonth(currentMonth, currentYear)) as _, index}
							{@const date = new Date(currentYear, currentMonth, index + 1)}
							{@const dayEvents = getEventsForDate(date)}
							<div
								class="group relative min-h-[3rem] cursor-pointer rounded-lg p-2 text-center transition-colors {isToday(
									date
								)
									? 'bg-white font-bold text-black'
									: 'bg-white/5 text-white hover:bg-white/10'}"
							>
								<span class="text-sm">{index + 1}</span>
								{#if dayEvents.length > 0}
									<div class="mt-1 flex justify-center space-x-1">
										{#each dayEvents.slice(0, 3) as event}
											<div class="h-1 w-1 rounded-full {eventTypes[event.type].color}"></div>
										{/each}
										{#if dayEvents.length > 3}
											<div class="h-1 w-1 rounded-full bg-gray-400"></div>
										{/if}
									</div>
								{/if}
							</div>
						{/each}
					</div>

					<!-- Legend -->
					<div class="mt-6 grid grid-cols-2 gap-2">
						{#each Object.entries(eventTypes) as [key, type]}
							<div class="flex items-center space-x-2">
								<div class="h-3 w-3 rounded-full {type.color}"></div>
								<span class="text-sm text-gray-300">{type.name}</span>
							</div>
						{/each}
					</div>
				</div>

				<!-- Event Stats -->
				<div class="mt-8 grid grid-cols-2 gap-4">
					<div
						class="rounded-2xl border border-white/10 bg-white/5 p-4 text-center backdrop-blur-md"
					>
						<div class="text-2xl font-bold text-white">150+</div>
						<div class="text-sm text-gray-400">Monthly Events</div>
					</div>
					<div
						class="rounded-2xl border border-white/10 bg-white/5 p-4 text-center backdrop-blur-md"
					>
						<div class="text-2xl font-bold text-white">85%</div>
						<div class="text-sm text-gray-400">Avg. Attendance</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Create Event CTA -->
		<div
			class="mt-20 transform text-center transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-2xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md"
			>
				<h4 class="mb-4 text-2xl font-bold text-white">Have an Event Idea?</h4>
				<p class="mb-6 text-gray-300">
					Our community thrives on member-led initiatives. Share your ideas and help create amazing
					experiences for everyone!
				</p>
				<button
					class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
				>
					Propose an Event
				</button>
			</div>
		</div>
	</div>
</section>
