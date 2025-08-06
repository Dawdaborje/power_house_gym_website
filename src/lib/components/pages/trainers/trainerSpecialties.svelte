<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let selectedSpecialty = 'strength';

	interface Specialty {
		id: string;
		name: string;
		description: string;
		icon: string;
		trainers: string[];
		benefits: string[];
		techniques: string[];
		idealFor: string[];
		backgroundImage: string;
	}

	const specialties: Specialty[] = [
		{
			id: 'strength',
			name: 'Strength Training',
			description:
				'Build raw power and muscle mass with our expert strength coaches who specialize in progressive overload and compound movements.',
			icon: '💪',
			trainers: ['Marcus Steel', 'Mike Rodriguez'],
			benefits: [
				'Increased muscle mass',
				'Enhanced bone density',
				'Improved metabolism',
				'Greater functional strength'
			],
			techniques: [
				'Progressive Overload',
				'Compound Movements',
				'Periodization',
				'Form Optimization'
			],
			idealFor: [
				'Beginners to strength training',
				'Athletes seeking power gains',
				'Anyone wanting to build muscle',
				'Those recovering from injury'
			],
			backgroundImage:
				'https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80'
		},
		{
			id: 'cardio',
			name: 'Cardio & Conditioning',
			description:
				'Improve cardiovascular health and endurance with high-energy workouts designed to maximize calorie burn and boost stamina.',
			icon: '🔥',
			trainers: ['Sarah Johnson'],
			benefits: [
				'Improved heart health',
				'Enhanced endurance',
				'Weight management',
				'Stress reduction'
			],
			techniques: ['HIIT Training', 'Circuit Training', 'Interval Protocols', 'Heart Rate Zones'],
			idealFor: [
				'Weight loss goals',
				'Endurance athletes',
				'Heart health improvement',
				'Stress management'
			],
			backgroundImage:
				'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80'
		},
		{
			id: 'functional',
			name: 'Functional Training',
			description:
				'Master movement patterns that translate to real-world activities and athletic performance with our functional movement experts.',
			icon: '⚡',
			trainers: ['Alex Chen'],
			benefits: [
				'Better daily movement',
				'Injury prevention',
				'Athletic performance',
				'Improved mobility'
			],
			techniques: [
				'Movement Screening',
				'Corrective Exercise',
				'Multi-planar Training',
				'Stability Work'
			],
			idealFor: ['Athletes', 'Injury prevention', 'Older adults', 'Movement quality improvement'],
			backgroundImage:
				'https://images.unsplash.com/photo-1534438327276-14e5300c3a48?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80'
		},
		{
			id: 'yoga',
			name: 'Yoga & Wellness',
			description:
				'Find balance, flexibility, and inner peace through our comprehensive yoga and mindfulness programs.',
			icon: '🧘',
			trainers: ['Emma Wilson'],
			benefits: [
				'Increased flexibility',
				'Stress reduction',
				'Mental clarity',
				'Better sleep quality'
			],
			techniques: ['Vinyasa Flow', 'Yin Yoga', 'Meditation', 'Breathwork'],
			idealFor: [
				'Stress management',
				'Flexibility goals',
				'Mental wellness',
				'Recovery enhancement'
			],
			backgroundImage:
				'https://images.unsplash.com/photo-1506629905607-c7a4e6d05e4c?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80'
		},
		{
			id: 'nutrition',
			name: 'Nutrition Coaching',
			description:
				'Transform your relationship with food and create sustainable eating habits with our certified nutrition specialists.',
			icon: '🥗',
			trainers: ['Lisa Park'],
			benefits: [
				'Sustainable weight management',
				'Improved energy levels',
				'Better food relationships',
				'Enhanced performance'
			],
			techniques: ['Habit Coaching', 'Macro Planning', 'Behavior Change', 'Meal Planning'],
			idealFor: [
				'Weight management',
				'Performance nutrition',
				'Habit formation',
				'Lifestyle changes'
			],
			backgroundImage:
				'https://images.unsplash.com/photo-1490645935967-10de6ba17061?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80'
		},
		{
			id: 'powerlifting',
			name: 'Powerlifting',
			description:
				'Master the big three lifts - squat, bench, and deadlift - with competition-level coaching and technique refinement.',
			icon: '🏋️',
			trainers: ['Marcus Steel', 'Mike Rodriguez'],
			benefits: [
				'Maximum strength gains',
				'Perfect technique',
				'Competition readiness',
				'Record-breaking potential'
			],
			techniques: [
				'Competition Prep',
				'Technique Analysis',
				'Periodized Programming',
				'Mental Training'
			],
			idealFor: [
				'Competitive powerlifters',
				'Strength enthusiasts',
				'Technique improvement',
				'Record seekers'
			],
			backgroundImage:
				'https://images.unsplash.com/photo-1583500178690-f7eb6bdecf5c?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80'
		}
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function selectSpecialty(specialtyId: string) {
		selectedSpecialty = specialtyId;
	}

	$: currentSpecialty = specialties.find((s) => s.id === selectedSpecialty) || specialties[0];
</script>

<section id="specialties" class="bg-black py-24">
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
				<span class="text-sm font-medium text-white/70">🎯 Areas of Expertise</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				TRAINER
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					SPECIALTIES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Our trainers bring specialized expertise across all areas of fitness. Find the perfect match
				for your specific goals and training style.
			</p>
		</div>

		<!-- Specialty Navigation -->
		<div
			class="mb-12 flex transform justify-center transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="flex flex-wrap justify-center gap-3 rounded-2xl border border-white/10 bg-white/5 p-3 backdrop-blur-md"
			>
				{#each specialties as specialty}
					<button
						on:click={() => selectSpecialty(specialty.id)}
						class="flex items-center space-x-2 rounded-xl px-4 py-2 text-sm font-semibold transition-all duration-300 {selectedSpecialty ===
						specialty.id
							? 'bg-white text-black shadow-lg'
							: 'text-white hover:bg-white/10'}"
					>
						<span>{specialty.icon}</span>
						<span class="hidden sm:inline">{specialty.name}</span>
					</button>
				{/each}
			</div>
		</div>

		<!-- Selected Specialty Details -->
		<div
			class="transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<!-- Hero Section for Selected Specialty -->
			<div class="relative mb-12 overflow-hidden rounded-3xl">
				<!-- Background Image -->
				<div class="relative h-96">
					<img
						src={currentSpecialty.backgroundImage}
						alt={currentSpecialty.name}
						class="h-full w-full object-cover"
					/>
					<div class="absolute inset-0 bg-black/70"></div>
					<div
						class="absolute inset-0 bg-gradient-to-r from-black/80 via-black/50 to-transparent"
					></div>
				</div>

				<!-- Content Overlay -->
				<div class="absolute inset-0 flex items-center">
					<div class="px-8 lg:px-16">
						<div class="max-w-2xl">
							<div class="mb-4 text-6xl">{currentSpecialty.icon}</div>
							<h3 class="mb-4 text-4xl font-black text-white md:text-5xl">
								{currentSpecialty.name}
							</h3>
							<p class="mb-6 text-xl leading-relaxed text-gray-300">
								{currentSpecialty.description}
							</p>
							<div class="flex flex-wrap items-center space-x-4">
								<span class="font-semibold text-white">Expert Trainers:</span>
								{#each currentSpecialty.trainers as trainer}
									<span class="rounded-full bg-white/20 px-3 py-1 text-sm font-medium text-white">
										{trainer}
									</span>
								{/each}
							</div>
						</div>
					</div>
				</div>
			</div>

			<!-- Specialty Details Grid -->
			<div class="grid grid-cols-1 gap-8 lg:grid-cols-3">
				<!-- Benefits -->
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<h4 class="mb-4 flex items-center space-x-2 text-xl font-bold text-white">
						<span>✨</span>
						<span>Benefits</span>
					</h4>
					<ul class="space-y-3">
						{#each currentSpecialty.benefits as benefit}
							<li class="flex items-start space-x-3">
								<div class="mt-1.5 h-2 w-2 rounded-full bg-white/60"></div>
								<span class="text-gray-300">{benefit}</span>
							</li>
						{/each}
					</ul>
				</div>

				<!-- Techniques -->
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<h4 class="mb-4 flex items-center space-x-2 text-xl font-bold text-white">
						<span>🔧</span>
						<span>Techniques</span>
					</h4>
					<ul class="space-y-3">
						{#each currentSpecialty.techniques as technique}
							<li class="flex items-start space-x-3">
								<div class="mt-1.5 h-2 w-2 rounded-full bg-white/60"></div>
								<span class="text-gray-300">{technique}</span>
							</li>
						{/each}
					</ul>
				</div>

				<!-- Ideal For -->
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<h4 class="mb-4 flex items-center space-x-2 text-xl font-bold text-white">
						<span>🎯</span>
						<span>Ideal For</span>
					</h4>
					<ul class="space-y-3">
						{#each currentSpecialty.idealFor as ideal}
							<li class="flex items-start space-x-3">
								<div class="mt-1.5 h-2 w-2 rounded-full bg-white/60"></div>
								<span class="text-gray-300">{ideal}</span>
							</li>
						{/each}
					</ul>
				</div>
			</div>

			<!-- CTA Section -->
			<div class="mt-12 text-center">
				<div
					class="mx-auto max-w-2xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md"
				>
					<h4 class="mb-4 text-2xl font-bold text-white">
						Ready to get started with {currentSpecialty.name}?
					</h4>
					<p class="mb-6 text-gray-300">
						Book a consultation with one of our {currentSpecialty.name.toLowerCase()} specialists.
					</p>
					<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
						<button
							class="rounded-xl bg-white px-6 py-3 font-bold text-black transition-colors duration-300 hover:bg-gray-200"
						>
							Book Consultation
						</button>
						<button
							class="rounded-xl border border-white/20 bg-white/10 px-6 py-3 font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
						>
							Learn More
						</button>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>
