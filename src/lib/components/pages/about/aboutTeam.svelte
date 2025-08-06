<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	interface TeamMember {
		id: string;
		name: string;
		position: string;
		department: string;
		bio: string;
		image: string;
		achievements: string[];
		specialties: string[];
		experience: string;
		certifications: string[];
		quote: string;
	}

	const leadershipTeam: TeamMember[] = [
		{
			id: 'marcus-steel',
			name: 'Marcus Steel',
			position: 'Co-Founder & CEO',
			department: 'Leadership',
			bio: 'Former Olympic weightlifter turned visionary entrepreneur. Marcus brings 15+ years of elite athletic experience and business acumen to Power House.',
			image:
				'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievements: [
				'Olympic Team Member 2012',
				'World Record Holder',
				'Fitness Industry Award Winner'
			],
			specialties: ['Strength Training', 'Olympic Lifting', 'Leadership'],
			experience: '15+ years',
			certifications: ['NSCA-CSCS', 'USAW Level 3', 'MBA'],
			quote: "Excellence is not a destination, it's a daily practice."
		},
		{
			id: 'sarah-johnson',
			name: 'Sarah Johnson',
			position: 'Co-Founder & COO',
			department: 'Leadership',
			bio: 'Marathon champion and operations expert who ensures every aspect of Power House runs smoothly while maintaining our high standards.',
			image:
				'https://images.unsplash.com/photo-1494790108755-2616b612b34c?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievements: [
				'Boston Marathon Winner',
				'Endurance Training Expert',
				'Operations Excellence Award'
			],
			specialties: ['Endurance Training', 'Operations', 'Member Experience'],
			experience: '12+ years',
			certifications: ['ACSM-CPT', 'RRCA Certified', 'Operations Management'],
			quote: "Every member's success is our success."
		},
		{
			id: 'dr-lisa-chen',
			name: 'Dr. Lisa Chen',
			position: 'Head of Wellness',
			department: 'Wellness',
			bio: 'Sports medicine physician and wellness expert who oversees our holistic approach to health and fitness.',
			image:
				'https://images.unsplash.com/photo-1559839734-2b71ea197ec2?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievements: [
				'Sports Medicine Board Certified',
				'Wellness Program Developer',
				'Research Publications'
			],
			specialties: ['Sports Medicine', 'Injury Prevention', 'Wellness Programs'],
			experience: '10+ years',
			certifications: ['MD Sports Medicine', 'ACSM Certified', 'Nutrition Specialist'],
			quote: 'True fitness encompasses mind, body, and spirit.'
		},
		{
			id: 'mike-rodriguez',
			name: 'Mike Rodriguez',
			position: 'Head Trainer',
			department: 'Training',
			bio: 'Former professional athlete who leads our training team with passion, expertise, and an unwavering commitment to member success.',
			image:
				'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievements: [
				'Pro Athlete Background',
				'Master Trainer Certified',
				'Team Development Expert'
			],
			specialties: ['Strength & Conditioning', 'Team Leadership', 'Performance Training'],
			experience: '8+ years',
			certifications: ['NSCA-CSCS', 'FMS Level 3', 'Precision Nutrition'],
			quote: 'Every rep, every set, every day matters.'
		}
	];

	const departments = [
		{
			name: 'Personal Training',
			description: 'Certified experts dedicated to your individual fitness journey',
			teamSize: 12,
			icon: '🏋️‍♂️',
			color: 'from-blue-500 to-blue-600'
		},
		{
			name: 'Group Fitness',
			description: 'Dynamic instructors who bring energy and motivation to every class',
			teamSize: 8,
			icon: '👥',
			color: 'from-green-500 to-green-600'
		},
		{
			name: 'Wellness & Recovery',
			description: 'Specialists in massage therapy, nutrition, and holistic wellness',
			teamSize: 6,
			icon: '🧘‍♀️',
			color: 'from-purple-500 to-purple-600'
		},
		{
			name: 'Member Services',
			description: 'Friendly faces who ensure your experience is exceptional every visit',
			teamSize: 10,
			icon: '🌟',
			color: 'from-yellow-500 to-yellow-600'
		},
		{
			name: 'Facility Operations',
			description: 'Behind-the-scenes heroes who keep everything running perfectly',
			teamSize: 8,
			icon: '🔧',
			color: 'from-red-500 to-red-600'
		},
		{
			name: 'Innovation Team',
			description: 'Tech-savvy professionals developing the future of fitness',
			teamSize: 4,
			icon: '💡',
			color: 'from-indigo-500 to-indigo-600'
		}
	];

	const teamStats = [
		{ label: 'Team Members', value: '50+', icon: '👥' },
		{ label: 'Combined Experience', value: '300+ years', icon: '⏰' },
		{ label: 'Professional Certifications', value: '200+', icon: '🏆' },
		{ label: 'Languages Spoken', value: '12', icon: '🌍' }
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
				<span class="text-sm font-medium text-white/70">👥 Meet the Experts</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				OUR ELITE
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					TEAM
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Meet the passionate professionals who make Power House Elite Fitness exceptional. Our team
				combines expertise, experience, and genuine care for every member's success.
			</p>
		</div>

		<!-- Team Stats -->
		<div
			class="mb-20 grid transform grid-cols-2 gap-6 transition-all delay-400 duration-1000 md:grid-cols-4 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each teamStats as stat, index}
				<div
					class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<div class="mb-3 text-3xl">{stat.icon}</div>
					<div class="mb-2 text-2xl font-bold text-white">{stat.value}</div>
					<div class="text-sm text-gray-400">{stat.label}</div>
				</div>
			{/each}
		</div>

		<!-- Leadership Team -->
		<div
			class="mb-20 transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Leadership Team</h3>
			<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
				{#each leadershipTeam as member, index}
					<div
						class="group rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10"
						style="transition-delay: {index * 150}ms"
					>
						<!-- Member Image -->
						<div class="mb-6 text-center">
							<div class="mx-auto h-32 w-32 overflow-hidden rounded-full">
								<img
									src={member.image}
									alt={member.name}
									class="h-full w-full object-cover transition-transform duration-300 group-hover:scale-105"
								/>
							</div>
						</div>

						<!-- Member Info -->
						<div class="text-center">
							<div class="mb-4">
								<h4 class="mb-2 text-2xl font-bold text-white">{member.name}</h4>
								<p class="mb-3 text-lg text-gray-400">{member.position}</p>
								<div class="inline-block rounded-full bg-white/10 px-4 py-2">
									<span class="text-sm font-medium text-white">{member.experience} experience</span>
								</div>
							</div>

							<p class="mb-6 leading-relaxed text-gray-300">{member.bio}</p>

							<!-- Quote -->
							<blockquote
								class="mb-6 border-l-4 border-white/20 pl-4 text-left text-gray-300 italic"
							>
								"{member.quote}"
							</blockquote>

							<!-- Specialties -->
							<div class="mb-6">
								<h5 class="mb-3 text-sm font-semibold tracking-wide text-white uppercase">
									Specialties
								</h5>
								<div class="flex flex-wrap justify-center gap-2">
									{#each member.specialties as specialty}
										<span class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white">
											{specialty}
										</span>
									{/each}
								</div>
							</div>

							<!-- Achievements -->
							<div>
								<h5 class="mb-3 text-sm font-semibold tracking-wide text-white uppercase">
									Key Achievements
								</h5>
								<div class="space-y-2 text-left">
									{#each member.achievements.slice(0, 3) as achievement}
										<div class="flex items-start space-x-2">
											<div class="mt-2 h-1 w-1 rounded-full bg-white/60"></div>
											<span class="text-sm text-gray-400">{achievement}</span>
										</div>
									{/each}
								</div>
							</div>
						</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- Departments -->
		<div
			class="mb-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Our Departments</h3>
			<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-3">
				{#each departments as dept, index}
					<div
						class="group relative overflow-hidden rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md transition-all duration-300 hover:border-white/20 hover:bg-white/10"
						style="transition-delay: {index * 100}ms"
					>
						<!-- Background Gradient -->
						<div
							class="absolute inset-0 bg-gradient-to-br {dept.color} opacity-5 transition-opacity duration-300 group-hover:opacity-10"
						></div>

						<!-- Content -->
						<div class="relative z-10 text-center">
							<div class="mb-4 text-4xl">{dept.icon}</div>
							<h4 class="mb-3 text-xl font-bold text-white">{dept.name}</h4>
							<p class="mb-4 text-gray-300">{dept.description}</p>
							<div class="inline-flex items-center rounded-full bg-white/10 px-3 py-1">
								<span class="text-sm font-medium text-white">{dept.teamSize} team members</span>
							</div>
						</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- Team Culture -->
		<div
			class="mb-20 transform transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-5xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md md:p-12"
			>
				<h3 class="mb-8 text-center text-3xl font-bold text-white">
					Why Our Team Chooses Power House
				</h3>
				<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
					<div class="space-y-6">
						<div class="flex items-start space-x-4">
							<div class="flex-shrink-0 text-2xl">🎓</div>
							<div>
								<h4 class="mb-2 text-lg font-bold text-white">Continuous Learning</h4>
								<p class="text-gray-300">
									We invest heavily in our team's education with ongoing training, certifications,
									and conference attendance.
								</p>
							</div>
						</div>

						<div class="flex items-start space-x-4">
							<div class="flex-shrink-0 text-2xl">🏆</div>
							<div>
								<h4 class="mb-2 text-lg font-bold text-white">Recognition & Growth</h4>
								<p class="text-gray-300">
									We celebrate achievements and provide clear career advancement paths for all team
									members.
								</p>
							</div>
						</div>

						<div class="flex items-start space-x-4">
							<div class="flex-shrink-0 text-2xl">🤝</div>
							<div>
								<h4 class="mb-2 text-lg font-bold text-white">Collaborative Environment</h4>
								<p class="text-gray-300">
									Our team works together as a family, supporting each other and sharing knowledge
									freely.
								</p>
							</div>
						</div>
					</div>

					<div class="space-y-6">
						<div class="flex items-start space-x-4">
							<div class="flex-shrink-0 text-2xl">💰</div>
							<div>
								<h4 class="mb-2 text-lg font-bold text-white">Competitive Benefits</h4>
								<p class="text-gray-300">
									Comprehensive benefits package including health insurance, retirement plans, and
									free gym membership.
								</p>
							</div>
						</div>

						<div class="flex items-start space-x-4">
							<div class="flex-shrink-0 text-2xl">🌟</div>
							<div>
								<h4 class="mb-2 text-lg font-bold text-white">Meaningful Work</h4>
								<p class="text-gray-300">
									Every day, our team members see the direct impact of their work on members' lives
									and transformations.
								</p>
							</div>
						</div>

						<div class="flex items-start space-x-4">
							<div class="flex-shrink-0 text-2xl">⚖️</div>
							<div>
								<h4 class="mb-2 text-lg font-bold text-white">Work-Life Balance</h4>
								<p class="text-gray-300">
									Flexible scheduling and time-off policies that respect our team's personal lives
									and well-being.
								</p>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Join Our Team CTA -->
		<div
			class="transform transition-all delay-1200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-3xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-4 text-2xl font-bold text-white">Want to Join Our Team?</h3>
				<p class="mb-6 text-gray-300">
					We're always looking for passionate, qualified professionals who share our values and
					commitment to excellence. Be part of something special.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						View Open Positions
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Learn About Benefits
					</button>
				</div>
			</div>
		</div>
	</div>
</section>
