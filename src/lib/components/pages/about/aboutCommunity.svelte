<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	const communityInitiatives = [
		{
			title: 'Free Community Fitness Classes',
			description:
				'Monthly outdoor fitness classes open to everyone, regardless of membership status.',
			impact: '500+ participants monthly',
			image:
				'https://images.unsplash.com/photo-1571902943202-507ec2618e8f?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			icon: '🏃‍♀️'
		},
		{
			title: 'Youth Fitness Programs',
			description:
				'Free after-school fitness programs for local teens, promoting healthy habits early.',
			impact: '200+ teens enrolled',
			image:
				'https://images.unsplash.com/photo-1594736797933-d0b22c6f3eae?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			icon: '👦'
		},
		{
			title: 'Senior Wellness Initiative',
			description:
				'Specialized fitness programs designed for seniors, focusing on mobility and health.',
			impact: '150+ seniors served',
			image:
				'https://images.unsplash.com/photo-1506629905607-c7a4e6d05e4c?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			icon: '👴'
		},
		{
			title: 'Charity Fundraising Events',
			description: 'Annual fitness challenges and events that raise money for local charities.',
			impact: '$50K+ raised annually',
			image:
				'https://images.unsplash.com/photo-1549476464-37392f717541?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			icon: '❤️'
		}
	];

	const partnerships = [
		{
			organization: 'Local Schools',
			partnership: 'PE Program Support',
			description:
				'Providing equipment and expertise to enhance school physical education programs.',
			duration: '3 years'
		},
		{
			organization: 'City Health Department',
			partnership: 'Public Health Initiative',
			description: 'Collaborating on city-wide wellness campaigns and health screenings.',
			duration: '4 years'
		},
		{
			organization: 'Food Bank Network',
			partnership: 'Healthy Food Drive',
			description: 'Monthly food drives focusing on nutritious options for families in need.',
			duration: '2 years'
		},
		{
			organization: 'Veterans Association',
			partnership: 'Fitness for Heroes',
			description: 'Free memberships and specialized programs for military veterans.',
			duration: '5 years'
		}
	];

	const volunteerStats = [
		{ number: '200+', label: 'Volunteer Hours/Month', icon: '⏰' },
		{ number: '25+', label: 'Community Events/Year', icon: '📅' },
		{ number: '1000+', label: 'People Served/Month', icon: '👥' },
		{ number: '15+', label: 'Partner Organizations', icon: '🤝' }
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
				<span class="text-sm font-medium text-white/70">🌍 Giving Back</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				COMMUNITY
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					IMPACT
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				We believe fitness should be accessible to everyone. Through our community initiatives,
				partnerships, and volunteer efforts, we're making a positive impact beyond our walls.
			</p>
		</div>

		<!-- Community Stats -->
		<div
			class="mb-20 grid transform grid-cols-2 gap-6 transition-all delay-400 duration-1000 md:grid-cols-4 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each volunteerStats as stat, index}
				<div
					class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<div class="mb-3 text-3xl">{stat.icon}</div>
					<div class="mb-2 text-2xl font-bold text-white">{stat.number}</div>
					<div class="text-sm text-gray-400">{stat.label}</div>
				</div>
			{/each}
		</div>

		<!-- Community Initiatives -->
		<div
			class="mb-20 transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Our Community Programs</h3>
			<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
				{#each communityInitiatives as initiative, index}
					<div
						class="group overflow-hidden rounded-3xl border border-white/10 bg-white/5 backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10"
						style="transition-delay: {index * 150}ms"
					>
						<!-- Image -->
						<div class="relative h-48 overflow-hidden">
							<img
								src={initiative.image}
								alt={initiative.title}
								class="h-full w-full object-cover transition-transform duration-300 group-hover:scale-105"
							/>
							<div
								class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent"
							></div>
							<div class="absolute bottom-4 left-4">
								<div class="flex items-center space-x-2">
									<div class="rounded-full bg-white/20 p-2 backdrop-blur-md">
										<span class="text-lg">{initiative.icon}</span>
									</div>
									<div class="rounded-full bg-white/20 px-3 py-1 backdrop-blur-md">
										<span class="text-sm font-medium text-white">{initiative.impact}</span>
									</div>
								</div>
							</div>
						</div>

						<!-- Content -->
						<div class="p-6">
							<h4
								class="mb-3 text-xl font-bold text-white transition-colors group-hover:text-gray-200"
							>
								{initiative.title}
							</h4>
							<p class="leading-relaxed text-gray-300">{initiative.description}</p>
						</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- Community Partnerships -->
		<div
			class="mb-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Community Partnerships</h3>
			<div class="grid grid-cols-1 gap-6 md:grid-cols-2">
				{#each partnerships as partnership, index}
					<div
						class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md transition-all duration-300 hover:bg-white/10"
						style="transition-delay: {index * 100}ms"
					>
						<div class="mb-4 flex items-start justify-between">
							<div>
								<h4 class="mb-1 text-lg font-bold text-white">{partnership.organization}</h4>
								<p class="text-sm text-gray-400">{partnership.partnership}</p>
							</div>
							<div class="rounded-full bg-white/10 px-3 py-1">
								<span class="text-xs font-medium text-white">{partnership.duration}</span>
							</div>
						</div>
						<p class="text-gray-300">{partnership.description}</p>
					</div>
				{/each}
			</div>
		</div>

		<!-- Volunteer Opportunities -->
		<div
			class="mb-20 transform transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-5xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md md:p-12"
			>
				<h3 class="mb-8 text-center text-3xl font-bold text-white">Get Involved</h3>
				<p class="mb-8 text-center text-lg text-gray-300">
					Join our team of dedicated volunteers and make a difference in your community while
					staying active and meeting like-minded people.
				</p>

				<div class="grid grid-cols-1 gap-6 md:grid-cols-3">
					<div class="text-center">
						<div class="mb-4 text-4xl">🏃‍♀️</div>
						<h4 class="mb-3 text-lg font-bold text-white">Event Volunteer</h4>
						<p class="text-gray-300">
							Help organize and run community fitness events, races, and health fairs.
						</p>
					</div>

					<div class="text-center">
						<div class="mb-4 text-4xl">🏫</div>
						<h4 class="mb-3 text-lg font-bold text-white">Youth Mentor</h4>
						<p class="text-gray-300">
							Guide and inspire young people in our after-school fitness programs.
						</p>
					</div>

					<div class="text-center">
						<div class="mb-4 text-4xl">🎯</div>
						<h4 class="mb-3 text-lg font-bold text-white">Outreach Ambassador</h4>
						<p class="text-gray-300">
							Represent Power House at community events and spread wellness awareness.
						</p>
					</div>
				</div>

				<div class="mt-8 text-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Join Our Volunteer Team
					</button>
				</div>
			</div>
		</div>

		<!-- Environmental Commitment -->
		<div
			class="mb-20 transform transition-all delay-1200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Environmental Responsibility</h3>
			<div class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-4">
				{#each [{ icon: '♻️', title: 'Recycling Program', description: '90% waste recycled monthly' }, { icon: '💡', title: 'Energy Efficiency', description: 'LED lighting throughout facility' }, { icon: '💧', title: 'Water Conservation', description: 'Low-flow fixtures installed' }, { icon: '🌱', title: 'Green Cleaning', description: 'Eco-friendly cleaning products only' }] as initiative, index}
					<div
						class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
						style="transition-delay: {index * 100}ms"
					>
						<div class="mb-4 text-3xl">{initiative.icon}</div>
						<h4 class="mb-3 text-lg font-bold text-white">{initiative.title}</h4>
						<p class="text-sm text-gray-300">{initiative.description}</p>
					</div>
				{/each}
			</div>
		</div>

		<!-- Member Testimonial -->
		<div
			class="transform transition-all delay-1400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/20 bg-gradient-to-r from-white/10 to-white/5 p-8 text-center backdrop-blur-md md:p-12"
			>
				<div class="mb-6 text-5xl">💬</div>
				<blockquote class="mb-6 text-2xl leading-relaxed text-white italic">
					"Power House doesn't just talk about community - they live it. Volunteering with their
					youth programs has been as rewarding for me as my personal fitness journey. It's amazing
					to be part of an organization that truly cares about making a difference."
				</blockquote>
				<div class="flex items-center justify-center space-x-4">
					<img
						src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=100&q=80"
						alt="Michael R."
						class="h-16 w-16 rounded-full object-cover"
					/>
					<div class="text-left">
						<div class="font-semibold text-white">Michael R.</div>
						<div class="text-sm text-gray-400">Member & Volunteer</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Get Involved CTA -->
		<div
			class="mt-16 transform text-center transition-all delay-1600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mx-auto max-w-2xl">
				<h4 class="mb-4 text-2xl font-bold text-white">Ready to Make a Difference?</h4>
				<p class="mb-6 text-gray-300">
					Join us in creating positive change in our community. Whether through volunteering,
					participating in events, or simply spreading the word, every action makes an impact.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Volunteer With Us
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						View Upcoming Events
					</button>
				</div>
			</div>
		</div>
	</div>
</section>
