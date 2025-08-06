<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	const milestones = [
		{
			year: '2018',
			title: 'The Beginning',
			description: 'Founded by fitness enthusiasts Marcus Steel and Sarah Johnson with a vision to create more than just another gym.',
			image: 'https://images.unsplash.com/photo-1571902943202-507ec2618e8f?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievement: 'First 100 members joined'
		},
		{
			year: '2019',
			title: 'Community Growth',
			description: 'Expanded to include group fitness classes and hired our first team of certified personal trainers.',
			image: 'https://images.unsplash.com/photo-1549476464-37392f717541?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievement: 'Reached 500 active members'
		},
		{
			year: '2020',
			title: 'Innovation & Adaptation',
			description: 'Introduced virtual training programs and enhanced safety protocols, keeping our community connected through challenging times.',
			image: 'https://images.unsplash.com/photo-1583500178690-f7eb6bdecf5c?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievement: 'Launched digital platform'
		},
		{
			year: '2021',
			title: 'Facility Expansion',
			description: 'Doubled our space with state-of-the-art equipment, recovery zones, and specialized training areas.',
			image: 'https://images.unsplash.com/photo-1534438327276-14e5300c3a48?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievement: '15,000 sq ft facility'
		},
		{
			year: '2022',
			title: 'Excellence Recognition',
			description: 'Named "Best Gym in the City" and achieved industry certifications for our training programs.',
			image: 'https://images.unsplash.com/photo-1571902943202-507ec2618e8f?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievement: 'Award-winning facility'
		},
		{
			year: '2024',
			title: 'Elite Status',
			description: 'Today, we continue to set the standard for premium fitness experiences with 2000+ members and counting.',
			image: 'https://images.unsplash.com/photo-1540497077202-7c8a3999166f?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			achievement: '2000+ member community'
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
				<span class="text-sm font-medium text-white/70">📖 Our Journey</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				THE POWER HOUSE
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					STORY
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				From a small vision to an elite fitness destination, discover the journey that made Power
				House the premier gym in the city.
			</p>
		</div>

		<!-- Mission Statement -->
		<div
			class="mb-20 transform transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-5xl rounded-3xl border border-white/20 bg-gradient-to-r from-white/10 to-white/5 p-8 text-center backdrop-blur-md md:p-12"
			>
				<h3 class="mb-6 text-3xl font-bold text-white">Our Mission</h3>
				<blockquote class="mb-8 text-2xl leading-relaxed text-gray-300 italic">
					"To empower every individual to unlock their full potential through innovative fitness
					solutions, expert guidance, and an unbreakable community spirit that transforms lives
					beyond the gym."
				</blockquote>
				<div class="flex items-center justify-center space-x-4">
					<div class="h-px w-16 bg-white/30"></div>
					<span class="text-white/70">Est. 2018</span>
					<div class="h-px w-16 bg-white/30"></div>
				</div>
			</div>
		</div>

		<!-- Timeline -->
		<div
			class="transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-16 text-center text-3xl font-bold text-white">Our Journey</h3>
			
			<!-- Desktop Timeline -->
			<div class="relative hidden lg:block">
				<!-- Timeline Line -->
				<div class="absolute left-1/2 top-0 h-full w-1 -translate-x-1/2 transform bg-gradient-to-b from-white via-gray-400 to-white"></div>
				
				<!-- Timeline Items -->
				<div class="space-y-24">
					{#each milestones as milestone, index}
						<div
							class="relative flex items-center {index % 2 === 0 ? 'flex-row' : 'flex-row-reverse'}"
							style="transition-delay: {200 + index * 100}ms"
						>
							<!-- Timeline Dot -->
							<div class="absolute left-1/2 z-10 flex h-16 w-16 -translate-x-1/2 transform items-center justify-center rounded-full border-4 border-white bg-black">
								<span class="text-lg font-bold text-white">{milestone.year}</span>
							</div>
							
							<!-- Content -->
							<div class="w-5/12 {index % 2 === 0 ? 'pr-16 text-right' : 'pl-16 text-left'}">
								<div class="rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md">
									<h4 class="mb-4 text-2xl font-bold text-white">{milestone.title}</h4>
									<p class="mb-4 text-gray-300 leading-relaxed">{milestone.description}</p>
									<div class="inline-block rounded-full bg-white/10 px-4 py-2">
										<span class="text-sm font-medium text-white">{milestone.achievement}</span>
									</div>
								</div>
							</div>
							
							<!-- Image -->
							<div class="w-5/12 {index % 2 === 0 ? 'pl-16' : 'pr-16'}">
								<div class="overflow-hidden rounded-2xl border border-white/10">
									<img
										src={milestone.image}
										alt={milestone.title}
										class="h-64 w-full object-cover transition-transform duration-300 hover:scale-105"
									/>
								</div>
							</div>
						</div>
					{/each}
				</div>
			</div>

			<!-- Mobile Timeline -->
			<div class="block lg:hidden">
				<div class="space-y-12">
					{#each milestones as milestone, index}
						<div
							class="relative rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md"
							style="transition-delay: {200 + index * 100}ms"
						>
							<div class="mb-4 flex items-center justify-between">
								<div class="rounded-full bg-white/20 px-4 py-2">
									<span class="text-lg font-bold text-white">{milestone.year}</span>
								</div>
								<div class="rounded-full bg-white/10 px-3 py-1">
									<span class="text-sm font-medium text-white">{milestone.achievement}</span>
								</div>
							</div>
							
							<div class="mb-4 overflow-hidden rounded-xl">
								<img
									src={milestone.image}
									alt={milestone.title}
									class="h-48 w-full object-cover"
								/>
							</div>
							
							<h4 class="mb-3 text-xl font-bold text-white">{milestone.title}</h4>
							<p class="text-gray-300 leading-relaxed">{milestone.description}</p>
						</div>
					{/each}
				</div>
			</div>
		</div>

		<!-- Founder Story -->
		<div
			class="mt-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="grid grid-cols-1 gap-12 lg:grid-cols-2">
				<!-- Founder Content -->
				<div class="flex flex-col justify-center">
					<h3 class="mb-6 text-3xl font-bold text-white">Meet Our Founders</h3>
					<p class="mb-6 text-lg text-gray-300 leading-relaxed">
						Marcus Steel and Sarah Johnson didn't just want to open another gym. As former competitive
						athletes who experienced firsthand how the right environment and community could transform
						lives, they envisioned something different.
					</p>
					<p class="mb-6 text-lg text-gray-300 leading-relaxed">
						"We wanted to create a space where everyone - from beginners to elite athletes - could
						push their limits, achieve their goals, and be part of something bigger than themselves,"
						says Marcus.
					</p>
					<p class="text-lg text-gray-300 leading-relaxed">
						Today, their vision lives on in every aspect of Power House Elite Fitness, from our
						world-class facilities to our passionate team of trainers who are committed to your success.
					</p>
				</div>
				
				<!-- Founder Images -->
				<div class="grid grid-cols-2 gap-6">
					<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md">
						<div class="mb-4 h-32 w-32 mx-auto overflow-hidden rounded-full">
							<img
								src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=300&q=80"
								alt="Marcus Steel"
								class="h-full w-full object-cover"
							/>
						</div>
						<h4 class="mb-2 text-lg font-bold text-white">Marcus Steel</h4>
						<p class="mb-3 text-sm text-gray-400">Co-Founder & CEO</p>
						<p class="text-xs text-gray-500">Former Olympic Weightlifter</p>
					</div>
					
					<div class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md">
						<div class="mb-4 h-32 w-32 mx-auto overflow-hidden rounded-full">
							<img
								src="https://images.unsplash.com/photo-1494790108755-2616b612b34c?ixlib=rb-4.0.3&auto=format&fit=crop&w=300&q=80"
								alt="Sarah Johnson"
								class="h-full w-full object-cover"
							/>
						</div>
						<h4 class="mb-2 text-lg font-bold text-white">Sarah Johnson</h4>
						<p class="mb-3 text-sm text-gray-400">Co-Founder & COO</p>
						<p class="text-xs text-gray-500">Former Marathon Champion</p>
					</div>
				</div>
			</div>
		</div>

		<!-- Vision for Future -->
		<div
			class="mt-20 transform transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-6 text-3xl font-bold text-white">Looking Ahead</h3>
				<p class="mb-8 text-lg text-gray-300 leading-relaxed">
					As we continue to grow, our commitment remains unchanged: to provide an unparalleled fitness
					experience that empowers every member to achieve their personal best. We're not just building
					stronger bodies - we're building stronger lives, stronger communities, and a stronger future.
				</p>
				<div class="grid grid-cols-1 gap-6 md:grid-cols-3">
					<div>
						<div class="mb-2 text-3xl">🌍</div>
						<div class="font-semibold text-white">Global Expansion</div>
						<div class="text-sm text-gray-400">Bringing Power House worldwide</div>
					</div>
					<div>
						<div class="mb-2 text-3xl">🔬</div>
						<div class="font-semibold text-white">Innovation Lab</div>
						<div class="text-sm text-gray-400">Pioneering fitness technology</div>
					</div>
					<div>
						<div class="mb-2 text-3xl">🏆</div>
						<div class="font-semibold text-white">Elite Academy</div>
						<div class="text-sm text-gray-400">Training future champions</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>