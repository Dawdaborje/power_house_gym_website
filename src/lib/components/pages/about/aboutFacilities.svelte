<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let selectedArea = 'cardio';

	const facilityAreas = [
		{
			id: 'cardio',
			name: 'Cardio Zone',
			description:
				'State-of-the-art cardiovascular equipment with entertainment systems and performance tracking.',
			features: [
				'50+ Cardio Machines',
				'Virtual Training Programs',
				'Heart Rate Monitoring',
				'Entertainment Systems'
			],
			image:
				'https://images.unsplash.com/photo-1571902943202-507ec2618e8f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			stats: { size: '3,000 sq ft', equipment: '50+ machines', capacity: '80 members' }
		},
		{
			id: 'strength',
			name: 'Strength Training',
			description:
				'Premium weight training area with Olympic platforms and specialized equipment for serious lifters.',
			features: [
				'Olympic Lifting Platforms',
				'Power Racks & Cages',
				'Free Weight Section',
				'Specialized Machines'
			],
			image:
				'https://images.unsplash.com/photo-1583500178690-f7eb6bdecf5c?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			stats: { size: '4,500 sq ft', equipment: '100+ pieces', capacity: '60 members' }
		},
		{
			id: 'functional',
			name: 'Functional Training',
			description:
				'Open space designed for functional movements, HIIT workouts, and athletic training.',
			features: [
				'Turf Training Area',
				'Suspension Systems',
				'Battle Ropes',
				'Plyometric Equipment'
			],
			image:
				'https://images.unsplash.com/photo-1534438327276-14e5300c3a48?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			stats: { size: '2,500 sq ft', equipment: '30+ tools', capacity: '40 members' }
		},
		{
			id: 'studios',
			name: 'Group Fitness Studios',
			description:
				'Multiple studios with professional sound systems and specialized flooring for all class types.',
			features: ['3 Dedicated Studios', 'Professional Sound', 'Mirrored Walls', 'Climate Control'],
			image:
				'https://images.unsplash.com/photo-1549476464-37392f717541?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			stats: { size: '2,000 sq ft', equipment: 'Full A/V setup', capacity: '30 per class' }
		},
		{
			id: 'recovery',
			name: 'Recovery Zone',
			description:
				'Dedicated space for stretching, mobility work, and recovery with premium amenities.',
			features: ['Sauna & Steam Rooms', 'Massage Therapy', 'Stretching Area', 'Recovery Tools'],
			image:
				'https://images.unsplash.com/photo-1506629905607-c7a4e6d05e4c?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			stats: { size: '1,500 sq ft', equipment: 'Recovery tools', capacity: '20 members' }
		}
	];

	const facilityHighlights = [
		{ icon: '🏢', title: '15,000 sq ft', description: 'Total facility space' },
		{ icon: '🔧', title: '200+ Equipment', description: 'Premium machines & tools' },
		{ icon: '🌡️', title: 'Climate Controlled', description: 'Optimal temperature year-round' },
		{ icon: '🔒', title: '24/7 Access', description: 'Train on your schedule' },
		{ icon: '🚿', title: 'Luxury Amenities', description: 'Premium locker rooms' },
		{ icon: '📱', title: 'Smart Technology', description: 'App-integrated equipment' }
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function selectArea(areaId: string) {
		selectedArea = areaId;
	}

	$: currentArea = facilityAreas.find((area) => area.id === selectedArea) || facilityAreas[0];
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
				<span class="text-sm font-medium text-white/70">🏢 World-Class Facilities</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				ELITE
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					FACILITIES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Step into a 15,000 square foot facility designed with your success in mind. Every detail has
				been carefully planned to provide the ultimate training environment.
			</p>
		</div>

		<!-- Facility Highlights -->
		<div
			class="mb-20 grid transform grid-cols-2 gap-6 transition-all delay-400 duration-1000 md:grid-cols-3 lg:grid-cols-6 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each facilityHighlights as highlight, index}
				<div
					class="rounded-2xl border border-white/10 bg-white/5 p-4 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<div class="mb-2 text-2xl">{highlight.icon}</div>
					<div class="mb-1 text-lg font-bold text-white">{highlight.title}</div>
					<div class="text-xs text-gray-400">{highlight.description}</div>
				</div>
			{/each}
		</div>

		<!-- Interactive Facility Tour -->
		<div
			class="mb-20 transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Virtual Facility Tour</h3>

			<!-- Area Selection -->
			<div class="mb-8 flex flex-wrap justify-center gap-2">
				{#each facilityAreas as area}
					<button
						on:click={() => selectArea(area.id)}
						class="rounded-xl px-4 py-2 text-sm font-semibold transition-all duration-300 {selectedArea ===
						area.id
							? 'bg-white text-black shadow-lg'
							: 'border border-white/20 bg-white/10 text-white hover:bg-white/20'}"
					>
						{area.name}
					</button>
				{/each}
			</div>

			<!-- Selected Area Display -->
			<div class="overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md">
				<div class="grid grid-cols-1 lg:grid-cols-2">
					<!-- Area Image -->
					<div class="relative h-96 lg:h-auto">
						<img
							src={currentArea.image}
							alt={currentArea.name}
							class="h-full w-full object-cover"
						/>
						<div
							class="absolute inset-0 bg-gradient-to-t from-black/40 via-transparent to-transparent lg:bg-gradient-to-r lg:from-transparent lg:to-black/40"
						></div>
					</div>

					<!-- Area Details -->
					<div class="p-8">
						<h4 class="mb-4 text-3xl font-bold text-white">{currentArea.name}</h4>
						<p class="mb-6 text-lg leading-relaxed text-gray-300">{currentArea.description}</p>

						<!-- Stats -->
						<div class="mb-6 grid grid-cols-3 gap-4">
							<div class="text-center">
								<div class="text-lg font-bold text-white">{currentArea.stats.size}</div>
								<div class="text-sm text-gray-400">Floor Space</div>
							</div>
							<div class="text-center">
								<div class="text-lg font-bold text-white">{currentArea.stats.equipment}</div>
								<div class="text-sm text-gray-400">Equipment</div>
							</div>
							<div class="text-center">
								<div class="text-lg font-bold text-white">{currentArea.stats.capacity}</div>
								<div class="text-sm text-gray-400">Capacity</div>
							</div>
						</div>

						<!-- Features -->
						<div class="mb-6">
							<h5 class="mb-3 text-lg font-semibold text-white">Key Features:</h5>
							<div class="grid grid-cols-2 gap-2">
								{#each currentArea.features as feature}
									<div class="flex items-center space-x-2">
										<svg class="h-4 w-4 text-green-400" fill="currentColor" viewBox="0 0 20 20">
											<path
												fill-rule="evenodd"
												d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
												clip-rule="evenodd"
											/>
										</svg>
										<span class="text-sm text-gray-300">{feature}</span>
									</div>
								{/each}
							</div>
						</div>

						<button
							class="w-full rounded-xl bg-white px-6 py-3 font-bold text-black transition-colors duration-300 hover:bg-gray-200"
						>
							Schedule Tour of {currentArea.name}
						</button>
					</div>
				</div>
			</div>
		</div>

		<!-- Equipment Showcase -->
		<div
			class="mb-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Premium Equipment</h3>
			<div class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-4">
				{#each [{ brand: 'Life Fitness', category: 'Cardio Equipment', count: '30+ machines' }, { brand: 'Hammer Strength', category: 'Strength Equipment', count: '40+ pieces' }, { brand: 'Rogue Fitness', category: 'Functional Training', count: '25+ tools' }, { brand: 'Keiser', category: 'Pneumatic Equipment', count: '15+ machines' }] as equipment, index}
					<div
						class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
						style="transition-delay: {index * 100}ms"
					>
						<div class="mb-4 text-3xl">🏋️‍♂️</div>
						<h4 class="mb-2 text-lg font-bold text-white">{equipment.brand}</h4>
						<p class="mb-2 text-sm text-gray-400">{equipment.category}</p>
						<p class="text-xs text-gray-500">{equipment.count}</p>
					</div>
				{/each}
			</div>
		</div>

		<!-- Safety & Cleanliness -->
		<div
			class="transform transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-5xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md md:p-12"
			>
				<h3 class="mb-8 text-center text-3xl font-bold text-white">
					Safety & Cleanliness Standards
				</h3>
				<div class="grid grid-cols-1 gap-8 md:grid-cols-3">
					<div class="text-center">
						<div class="mb-4 text-4xl">🧽</div>
						<h4 class="mb-3 text-lg font-bold text-white">Deep Cleaning Protocol</h4>
						<p class="text-gray-300">
							Equipment sanitized hourly with hospital-grade disinfectants. Full facility deep clean
							nightly.
						</p>
					</div>

					<div class="text-center">
						<div class="mb-4 text-4xl">🛡️</div>
						<h4 class="mb-3 text-lg font-bold text-white">Safety First</h4>
						<p class="text-gray-300">
							Regular equipment maintenance, safety inspections, and trained staff on-site 24/7.
						</p>
					</div>

					<div class="text-center">
						<div class="mb-4 text-4xl">🌬️</div>
						<h4 class="mb-3 text-lg font-bold text-white">Air Quality</h4>
						<p class="text-gray-300">
							Advanced HVAC system with HEPA filtration ensures optimal air quality throughout the
							facility.
						</p>
					</div>
				</div>
			</div>
		</div>

		<!-- Tour CTA -->
		<div
			class="mt-16 transform text-center transition-all delay-1200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mx-auto max-w-2xl">
				<h4 class="mb-4 text-2xl font-bold text-white">Ready to Experience Our Facilities?</h4>
				<p class="mb-6 text-gray-300">
					The best way to appreciate our facilities is to see them in person. Schedule a tour and
					discover why Power House is the premier choice for serious fitness enthusiasts.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Schedule Facility Tour
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Virtual 360° Tour
					</button>
				</div>
			</div>
		</div>
	</div>
</section>
