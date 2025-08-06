<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let selectedTrainer: string | null = null;

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
		hourlyRate: string;
		availability: string[];
		languages: string[];
		education: string[];
		philosophy: string;
	}

	const trainers: Trainer[] = [
		{
			id: 'marcus-steel',
			name: 'Marcus Steel',
			title: 'Senior Strength Coach & Performance Director',
			specialties: ['Powerlifting', 'Strength Training', 'Athletic Performance', 'Competition Prep'],
			experience: '8+ years',
			certifications: ['NSCA-CSCS', 'NASM-PES', 'USA Powerlifting Level 2', 'FMS Level 2'],
			image: 'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'Former competitive powerlifter with a passion for helping others reach their strength potential. Marcus specializes in compound movements and progressive overload training, with a proven track record of helping clients achieve record-breaking lifts.',
			programs: ['Beast Mode', 'Power Lifting', 'Strength Foundations'],
			achievements: [
				'National Powerlifting Champion 2019',
				'500+ successful transformations',
				'Certified Elite Trainer',
				'1200lb+ Raw Total (Personal Best)'
			],
			hourlyRate: '$120',
			availability: ['Mon-Fri 6:00 AM - 2:00 PM', 'Sat 8:00 AM - 12:00 PM'],
			languages: ['English', 'Spanish'],
			education: ['Exercise Science - University of Texas', 'Strength & Conditioning - NSCA'],
			philosophy: 'Strength is not just physical - it\'s mental, emotional, and spiritual. My goal is to help you discover the strongest version of yourself.'
		},
		{
			id: 'sarah-johnson',
			name: 'Sarah Johnson',
			title: 'Cardio & Conditioning Specialist',
			specialties: ['HIIT Training', 'Cardio Conditioning', 'Fat Loss', 'Endurance Training'],
			experience: '6+ years',
			certifications: ['ACSM-CPT', 'HIIT Specialist', 'TRX Certified', 'Precision Nutrition L1'],
			image: 'https://images.unsplash.com/photo-1594381898411-846e7d193883?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'High-energy trainer who brings infectious enthusiasm to every class. Sarah\'s cardio programs are designed to maximize calorie burn while keeping workouts fun and engaging. Former marathon runner turned fitness expert.',
			programs: ['Cardio Blast', 'HIIT Warrior', 'Metabolic Conditioning'],
			achievements: [
				'Marathon Runner (3:15 PR)',
				'300+ class completions',
				'Fitness Transformation Specialist',
				'HIIT Instructor of the Year 2022'
			],
			hourlyRate: '$95',
			availability: ['Tue-Sat 5:00 AM - 1:00 PM', 'Mon 12:00 PM - 8:00 PM'],
			languages: ['English', 'French'],
			education: ['Kinesiology - UCLA', 'Sports Nutrition Certification'],
			philosophy: 'Fitness should be fun, challenging, and sustainable. I believe in creating workouts that you\'ll actually look forward to.'
		},
		{
			id: 'alex-chen',
			name: 'Alex Chen',
			title: 'Functional Training & Mobility Expert',
			specialties: ['Functional Movement', 'HIIT', 'Athletic Training', 'Injury Prevention'],
			experience: '7+ years',
			certifications: ['NASM-CPT', 'FMS Level 2', 'Kettlebell Certified', 'SFMA Certified'],
			image: 'https://images.unsplash.com/photo-1607962837359-5e7e89f86776?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'Former competitive athlete turned trainer, Alex focuses on functional movements that translate to real-world performance and injury prevention. Specializes in corrective exercise and movement optimization.',
			programs: ['HIIT Warrior', 'Functional Fitness', 'Athletic Performance'],
			achievements: [
				'Former D1 Athlete (Track & Field)',
				'Functional Movement Expert',
				'400+ training sessions',
				'Mobility & Corrective Exercise Specialist'
			],
			hourlyRate: '$110',
			availability: ['Mon-Thu 7:00 AM - 3:00 PM', 'Fri-Sat 6:00 AM - 12:00 PM'],
			languages: ['English', 'Mandarin', 'Cantonese'],
			education: ['Exercise Physiology - Stanford', 'Corrective Exercise Specialist'],
			philosophy: 'Movement is medicine. I help you move better, feel better, and perform better in everything you do.'
		},
		{
			id: 'emma-wilson',
			name: 'Emma Wilson',
			title: 'Yoga & Wellness Director',
			specialties: ['Yoga', 'Flexibility', 'Mind-Body Connection', 'Stress Management'],
			experience: '10+ years',
			certifications: ['RYT-500', 'Yin Yoga Certified', 'Meditation Teacher', 'Trauma-Informed Yoga'],
			image: 'https://images.unsplash.com/photo-1518611012118-696072aa579a?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'Experienced yoga instructor who brings mindfulness and balance to fitness. Emma helps members develop flexibility, strength, and mental clarity through various yoga practices and meditation techniques.',
			programs: ['Yoga Flow', 'Recovery Sessions', 'Mindfulness Training'],
			achievements: [
				'500-Hour Yoga Certification',
				'Mindfulness Expert',
				'1000+ yoga classes taught',
				'Wellness Workshop Leader'
			],
			hourlyRate: '$85',
			availability: ['Daily 6:00 AM - 10:00 AM', 'Mon-Wed-Fri 5:00 PM - 9:00 PM'],
			languages: ['English', 'Hindi', 'Sanskrit'],
			education: ['Philosophy - UC Berkeley', 'Yoga Studies - Rishikesh, India'],
			philosophy: 'Yoga is not about perfection, it\'s about connection - to yourself, to others, and to the present moment.'
		},
		{
			id: 'mike-rodriguez',
			name: 'Mike Rodriguez',
			title: 'Powerlifting & Strength Specialist',
			specialties: ['Powerlifting', 'Olympic Lifting', 'Strength Training', 'Form Correction'],
			experience: '9+ years',
			certifications: ['USAPL Certified', 'NSCA-CSCS', 'Olympic Lifting L2', 'Precision Nutrition'],
			image: 'https://images.unsplash.com/photo-1583500178690-f7eb6bdecf5c?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'Powerlifting competitor and strength coach with extensive experience in Olympic lifting. Mike focuses on perfecting technique and building raw strength through progressive programming.',
			programs: ['Power Lifting', 'Olympic Lifting', 'Strength Fundamentals'],
			achievements: [
				'USAPL National Qualifier',
				'600lb+ Deadlift (Personal Best)',
				'Powerlifting Coach of the Year 2021',
				'Olympic Lifting Instructor'
			],
			hourlyRate: '$115',
			availability: ['Tue-Sat 5:00 AM - 1:00 PM', 'Thu 4:00 PM - 8:00 PM'],
			languages: ['English', 'Spanish', 'Portuguese'],
			education: ['Sports Science - Texas A&M', 'Biomechanics Specialty'],
			philosophy: 'Strength is earned through consistency, dedication, and respect for the iron. Every rep counts.'
		},
		{
			id: 'lisa-park',
			name: 'Lisa Park',
			title: 'Nutrition & Lifestyle Coach',
			specialties: ['Nutrition Coaching', 'Weight Management', 'Lifestyle Design', 'Habit Formation'],
			experience: '5+ years',
			certifications: ['Precision Nutrition L2', 'Certified Nutritionist', 'Behavior Change Specialist'],
			image: 'https://images.unsplash.com/photo-1594381898411-846e7d193883?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
			bio: 'Registered nutritionist who specializes in sustainable lifestyle changes. Lisa helps clients develop healthy relationships with food and create lasting habits for optimal health and performance.',
			programs: ['Nutrition Coaching', 'Lifestyle Design', 'Habit Coaching'],
			achievements: [
				'Registered Dietitian',
				'200+ nutrition transformations',
				'Behavior Change Expert',
				'Wellness Seminar Speaker'
			],
			hourlyRate: '$90',
			availability: ['Mon-Fri 9:00 AM - 5:00 PM', 'Virtual consultations available'],
			languages: ['English', 'Korean'],
			education: ['Nutrition Science - NYU', 'Psychology Minor'],
			philosophy: 'Sustainable change comes from understanding yourself, not following rigid rules. Let\'s build habits that fit your life.'
		}
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function selectTrainer(trainerId: string) {
		selectedTrainer = selectedTrainer === trainerId ? null : trainerId;
	}
</script>

<section id="profiles" class="bg-black py-24">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<!-- Section Header -->
		<div
			class="mb-20 text-center transform transition-all delay-200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mb-6 inline-flex items-center rounded-full border border-white/10 bg-white/5 px-6 py-2">
				<span class="text-sm font-medium text-white/70">👥 Meet Our Team</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				TRAINER 
				<span class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent">
					PROFILES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Get to know our certified fitness professionals who are dedicated to helping you achieve your goals with personalized guidance and expertise.
			</p>
		</div>

		<!-- Trainers Grid -->
		<div 
			class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-3 transform transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each trainers as trainer, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md transition-all duration-500 hover:scale-105 hover:border-white/20 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<!-- Trainer Image -->
					<div class="relative h-80 overflow-hidden">
						<img
							src={trainer.image}
							alt={trainer.name}
							class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
						/>
						<div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/20 to-transparent"></div>
						
						<!-- Rate Badge -->
						<div class="absolute top-4 right-4">
							<div class="rounded-full bg-white/20 px-3 py-1 backdrop-blur-md">
								<span class="text-xs font-medium text-white">{trainer.hourlyRate}/hour</span>
							</div>
						</div>

						<!-- Experience Badge -->
						<div class="absolute top-4 left-4">
							<div class="rounded-full bg-black/60 px-3 py-1 backdrop-blur-md">
								<span class="text-xs font-medium text-white">{trainer.experience}</span>
							</div>
						</div>

						<!-- Name & Title Overlay -->
						<div class="absolute bottom-4 left-4 right-4">
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
								{#each trainer.specialties.slice(0, 3) as specialty}
									<span class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white/80">
										{specialty}
									</span>
								{/each}
								{#if trainer.specialties.length > 3}
									<span class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white/60">
										+{trainer.specialties.length - 3} more
									</span>
								{/if}
							</div>
						</div>

						<!-- Quick Stats -->
						<div class="mb-6 space-y-2">
							<div class="flex items-center justify-between text-sm">
								<span class="text-gray-400">Languages:</span>
								<span class="text-white">{trainer.languages.join(', ')}</span>
							</div>
							<div class="flex items-center justify-between text-sm">
								<span class="text-gray-400">Certifications:</span>
								<span class="text-white">{trainer.certifications.length}</span>
							</div>
						</div>

						<!-- Action Buttons -->
						<div class="space-y-3">
							<button 
								on:click={() => selectTrainer(trainer.id)}
								class="w-full rounded-xl border border-white/20 bg-white/10 px-4 py-3 text-sm font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
							>
								{selectedTrainer === trainer.id ? 'Hide Details' : 'View Details'}
							</button>
							<button class="w-full rounded-xl bg-white px-4 py-3 text-sm font-bold text-black transition-colors duration-300 hover:bg-gray-200">
								Book Session
							</button>
						</div>
					</div>
				</div>

				<!-- Expanded Details Modal -->
				{#if selectedTrainer === trainer.id}
					<div 
						class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/80 backdrop-blur-sm"
						on:click={() => selectTrainer('')}
					>
						<div 
							class="max-w-4xl w-full max-h-[90vh] overflow-y-auto rounded-3xl border border-white/20 bg-black/95 backdrop-blur-md"
							on:click|stopPropagation
						>
							<div class="p-8">
								<!-- Header -->
								<div class="flex items-start justify-between mb-8">
									<div class="flex items-center space-x-6">
										<img
											src={trainer.image}
											alt={trainer.name}
											class="h-24 w-24 rounded-2xl object-cover"
										/>
										<div>
											<h3 class="text-3xl font-bold text-white">{trainer.name}</h3>
											<p class="text-lg text-gray-300">{trainer.title}</p>
											<p class="text-sm text-white/70">{trainer.hourlyRate}/hour • {trainer.experience}</p>
										</div>
									</div>
									<button 
										on:click={() => selectTrainer('')}
										class="rounded-full bg-white/10 p-2 text-white hover:bg-white/20 transition-colors"
									>
										<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
											<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
										</svg>
									</button>
								</div>

								<!-- Content Grid -->
								<div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
									<!-- Left Column -->
									<div class="space-y-6">
										<!-- Philosophy -->
										<div>
											<h4 class="mb-3 text-lg font-semibold text-white">Training Philosophy</h4>
											<p class="text-gray-300 italic">"{trainer.philosophy}"</p>
										</div>

										<!-- Education -->
										<div>
											<h4 class="mb-3 text-lg font-semibold text-white">Education</h4>
											<ul class="space-y-2">
												{#each trainer.education as edu}
													<li class="flex items-center space-x-2">
														<div class="h-1.5 w-1.5 rounded-full bg-white/60"></div>
														<span class="text-gray-300">{edu}</span>
													</li>
												{/each}
											</ul>
										</div>

										<!-- Availability -->
										<div>
											<h4 class="mb-3 text-lg font-semibold text-white">Availability</h4>
											<ul class="space-y-2">
												{#each trainer.availability as time}
													<li class="flex items-center justify-between rounded-lg bg-white/5 px-3 py-2">
														<span class="text-gray-300">{time}</span>
														<span class="text-xs text-green-400">Available</span>
													</li>
												{/each}
											</ul>
										</div>
									</div>

									<!-- Right Column -->
									<div class="space-y-6">
										<!-- All Specialties -->
										<div>
											<h4 class="mb-3 text-lg font-semibold text-white">All Specialties</h4>
											<div class="flex flex-wrap gap-2">
												{#each trainer.specialties as specialty}
													<span class="rounded-full bg-white/10 px-3 py-1 text-sm font-medium text-white/80">
														{specialty}
													</span>
												{/each}
											</div>
										</div>

										<!-- Certifications -->
										<div>
											<h4 class="mb-3 text-lg font-semibold text-white">Certifications</h4>
											<div class="grid grid-cols-2 gap-2">
												{#each trainer.certifications as cert}
													<span class="rounded bg-white/10 px-2 py-1 text-xs text-white/70">
														{cert}
													</span>
												{/each}
											</div>
										</div>

										<!-- Achievements -->
										<div>
											<h4 class="mb-3 text-lg font-semibold text-white">Achievements</h4>
											<ul class="space-y-2">
												{#each trainer.achievements as achievement}
													<li class="flex items-center space-x-2">
														<svg class="h-4 w-4 text-yellow-400" fill="currentColor" viewBox="0 0 24 24">
															<path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
														</svg>
														<span class="text-gray-300">{achievement}</span>
													</li>
												{/each}
											</ul>
										</div>

										<!-- Programs -->
										<div>
											<h4 class="mb-3 text-lg font-semibold text-white">Programs Led</h4>
											<ul class="space-y-1">
												{#each trainer.programs as program}
													<li class="flex items-center space-x-2">
														<div class="h-1.5 w-1.5 rounded-full bg-white/60"></div>
														<span class="text-gray-300">{program}</span>
													</li>
												{/each}
											</ul>
										</div>
									</div>
								</div>

								<!-- Action Footer -->
								<div class="mt-8 flex space-x-4">
									<button class="flex-1 rounded-xl bg-white px-6 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200">
										Book Session with {trainer.name.split(' ')[0]}
									</button>
									<button class="rounded-xl border border-white/20 bg-white/10 px-6 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black">
										Message
									</button>
								</div>
							</div>
						</div>
					</div>
				{/if}
			{/each}
		</div>
	</div>
</section>