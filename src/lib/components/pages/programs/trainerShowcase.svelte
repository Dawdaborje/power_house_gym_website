<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	interface Trainer {
		id: string;
		name: string;
		title: string;
		specialties: string[];
		experience: string;
		certifications: string[];
		image: string;
		bio: string;
		programs: string[];
		achievements: string[];
	}

	const trainers: Trainer[] = [
		{
			id: 'marcus-steel',
			name: 'Marcus Steel',
			title: 'Senior Strength Coach',
			specialties: ['Powerlifting', 'Strength Training', 'Athletic Performance'],
			experience: '8+ years',
			certifications: ['NSCA-CSCS', 'NASM-PES', 'USA Powerlifting'],
			image:
				'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'Former competitive powerlifter with a passion for helping others reach their strength potential. Marcus specializes in compound movements and progressive overload training.',
			programs: ['Beast Mode', 'Power Lifting'],
			achievements: [
				'National Powerlifting Champion 2019',
				'500+ successful transformations',
				'Certified Elite Trainer'
			]
		},
		{
			id: 'sarah-johnson',
			name: 'Sarah Johnson',
			title: 'Cardio & Conditioning Expert',
			specialties: ['HIIT Training', 'Cardio Conditioning', 'Fat Loss'],
			experience: '6+ years',
			certifications: ['ACSM-CPT', 'HIIT Specialist', 'TRX Certified'],
			image:
				'https://images.unsplash.com/photo-1594381898411-846e7d193883?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: "High-energy trainer who brings infectious enthusiasm to every class. Sarah's cardio programs are designed to maximize calorie burn while keeping workouts fun and engaging.",
			programs: ['Cardio Blast', 'HIIT Warrior'],
			achievements: [
				'Marathon Runner',
				'300+ class completions',
				'Fitness Transformation Specialist'
			]
		},
		{
			id: 'alex-chen',
			name: 'Alex Chen',
			title: 'HIIT & Functional Training Specialist',
			specialties: ['Functional Movement', 'HIIT', 'Athletic Training'],
			experience: '7+ years',
			certifications: ['NASM-CPT', 'FMS Level 2', 'Kettlebell Certified'],
			image:
				'https://images.unsplash.com/photo-1607962837359-5e7e89f86776?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'Former competitive athlete turned trainer, Alex focuses on functional movements that translate to real-world performance and injury prevention.',
			programs: ['HIIT Warrior', 'Functional Fitness'],
			achievements: ['Former D1 Athlete', 'Functional Movement Expert', '400+ training sessions']
		},
		{
			id: 'emma-wilson',
			name: 'Emma Wilson',
			title: 'Yoga & Recovery Specialist',
			specialties: ['Yoga', 'Flexibility', 'Mind-Body Connection'],
			experience: '10+ years',
			certifications: ['RYT-500', 'Yin Yoga Certified', 'Meditation Teacher'],
			image:
				'https://images.unsplash.com/photo-1518611012118-696072aa579a?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'Experienced yoga instructor who brings mindfulness and balance to fitness. Emma helps members develop flexibility, strength, and mental clarity through yoga practice.',
			programs: ['Yoga Flow', 'Recovery Sessions'],
			achievements: [
				'500-Hour Yoga Certification',
				'Mindfulness Expert',
				'1000+ yoga classes taught'
			]
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
		<div class="mb-20 text-center">
			<div
				class="mb-6 inline-flex items-center rounded-full border border-white/10 bg-white/5 px-6 py-2"
			>
				<span class="text-sm font-medium text-white/70">💪 Meet Your Trainers</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				EXPERT
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					TRAINERS
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Our certified fitness professionals are dedicated to helping you achieve your goals with
				personalized guidance and expertise.
			</p>
		</div>

		<!-- Trainers Grid -->
		<div class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-4">
			{#each trainers as trainer, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md transition-all duration-500 hover:scale-105 hover:border-white/20 hover:bg-white/10"
					style="transition-delay: {index * 150}ms"
				>
					<!-- Trainer Image -->
					<div class="relative h-80 overflow-hidden">
						<img
							src={trainer.image}
							alt={trainer.name}
							class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
						/>
						<div
							class="absolute inset-0 bg-gradient-to-t from-black/80 via-black/20 to-transparent"
						></div>

						<!-- Experience Badge -->
						<div class="absolute top-4 right-4">
							<div class="rounded-full bg-white/20 px-3 py-1 backdrop-blur-md">
								<span class="text-xs font-medium text-white">{trainer.experience}</span>
							</div>
						</div>

						<!-- Name & Title Overlay -->
						<div class="absolute right-4 bottom-4 left-4">
							<h3 class="mb-1 text-xl font-bold text-white">{trainer.name}</h3>
							<p class="text-sm text-gray-300">{trainer.title}</p>
						</div>
					</div>

					<!-- Trainer Info -->
					<div class="p-6">
						<!-- Bio -->
						<p class="mb-4 text-sm leading-relaxed text-gray-300">
							{trainer.bio}
						</p>

						<!-- Specialties -->
						<div class="mb-4">
							<h4 class="mb-2 text-sm font-semibold text-white">Specialties:</h4>
							<div class="flex flex-wrap gap-2">
								{#each trainer.specialties as specialty}
									<span
										class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white/80"
									>
										{specialty}
									</span>
								{/each}
							</div>
						</div>

						<!-- Programs -->
						<div class="mb-4">
							<h4 class="mb-2 text-sm font-semibold text-white">Programs:</h4>
							<div class="space-y-1">
								{#each trainer.programs as program}
									<div class="flex items-center space-x-2">
										<div class="h-1.5 w-1.5 rounded-full bg-white/60"></div>
										<span class="text-xs text-gray-300">{program}</span>
									</div>
								{/each}
							</div>
						</div>

						<!-- Certifications -->
						<div class="mb-6">
							<h4 class="mb-2 text-sm font-semibold text-white">Certifications:</h4>
							<div class="flex flex-wrap gap-1">
								{#each trainer.certifications as cert}
									<span class="rounded bg-white/10 px-2 py-1 text-xs text-white/70">
										{cert}
									</span>
								{/each}
							</div>
						</div>

						<!-- Achievements -->
						<div class="mb-6">
							<h4 class="mb-2 text-sm font-semibold text-white">Achievements:</h4>
							<div class="space-y-1">
								{#each trainer.achievements as achievement}
									<div class="flex items-center space-x-2">
										<svg class="h-3 w-3 text-yellow-400" fill="currentColor" viewBox="0 0 24 24">
											<path
												d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
											/>
										</svg>
										<span class="text-xs text-gray-300">{achievement}</span>
									</div>
								{/each}
							</div>
						</div>

						<!-- Contact Button -->
						<button
							class="w-full rounded-xl bg-white px-4 py-3 text-sm font-bold text-black transition-colors duration-300 hover:bg-gray-200"
						>
							Book Session
						</button>
					</div>

					<!-- Hover Overlay -->
					<div
						class="absolute inset-0 opacity-0 transition-opacity duration-300 group-hover:opacity-100"
					>
						<div
							class="absolute inset-0 bg-gradient-to-t from-black/10 via-transparent to-transparent"
						></div>
					</div>
				</div>
			{/each}
		</div>

		<!-- Trainer Stats -->
		<div
			class="mt-20 transform text-center transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="grid grid-cols-1 gap-8 md:grid-cols-4">
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-2 text-3xl font-black text-white">12+</div>
					<div class="text-sm font-medium text-gray-300">Expert Trainers</div>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-2 text-3xl font-black text-white">50+</div>
					<div class="text-sm font-medium text-gray-300">Certifications</div>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-2 text-3xl font-black text-white">5000+</div>
					<div class="text-sm font-medium text-gray-300">Training Sessions</div>
				</div>
				<div class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
					<div class="mb-2 text-3xl font-black text-white">98%</div>
					<div class="text-sm font-medium text-gray-300">Client Satisfaction</div>
				</div>
			</div>
		</div>

		<!-- Personal Training CTA -->
		<div
			class="mt-16 transform text-center transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md md:p-12"
			>
				<h3 class="mb-4 text-3xl font-black text-white md:text-4xl">
					Ready for Personal Training?
				</h3>
				<p class="mb-8 text-xl text-gray-300">
					Get one-on-one attention with a customized workout plan designed specifically for your
					goals.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-2xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Book Consultation
					</button>
					<button
						class="rounded-2xl border-2 border-white bg-transparent px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Learn More
					</button>
				</div>
			</div>
		</div>
	</div>
</section>
