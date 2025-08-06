<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	const coreValues = [
		{
			icon: '🎯',
			title: 'Excellence',
			description:
				'We pursue excellence in everything we do, from our equipment and facilities to our training programs and customer service.',
			principles: [
				'Highest quality equipment and maintenance',
				'Continuous education and certification',
				'Exceeding member expectations daily',
				'Innovation in fitness solutions'
			],
			color: 'from-blue-500 to-blue-600'
		},
		{
			icon: '🤝',
			title: 'Community',
			description:
				'We believe in the power of community to motivate, inspire, and support each member on their fitness journey.',
			principles: [
				'Inclusive and welcoming environment',
				'Mutual support and encouragement',
				'Building lasting friendships',
				'Celebrating shared achievements'
			],
			color: 'from-green-500 to-green-600'
		},
		{
			icon: '💪',
			title: 'Transformation',
			description:
				'We are committed to helping every member transform not just their body, but their mindset and lifestyle.',
			principles: [
				'Personalized fitness journeys',
				'Holistic approach to wellness',
				'Sustainable lifestyle changes',
				'Mental and physical empowerment'
			],
			color: 'from-red-500 to-red-600'
		},
		{
			icon: '🚀',
			title: 'Innovation',
			description:
				'We stay at the forefront of fitness trends and technology to provide cutting-edge solutions for our members.',
			principles: [
				'Latest fitness technology integration',
				'Progressive training methodologies',
				'Data-driven performance tracking',
				'Continuous facility improvements'
			],
			color: 'from-purple-500 to-purple-600'
		},
		{
			icon: '🌟',
			title: 'Integrity',
			description:
				'We operate with complete transparency, honesty, and ethical practices in all our interactions.',
			principles: [
				'Transparent pricing and policies',
				'Honest fitness advice and guidance',
				'Ethical business practices',
				'Keeping promises to our community'
			],
			color: 'from-yellow-500 to-yellow-600'
		},
		{
			icon: '⚡',
			title: 'Empowerment',
			description:
				'We empower our members with knowledge, tools, and confidence to take control of their health and fitness.',
			principles: [
				'Education-focused approach',
				'Building self-confidence',
				'Encouraging independence',
				'Fostering personal growth'
			],
			color: 'from-indigo-500 to-indigo-600'
		}
	];

	const culturalAspects = [
		{
			title: 'Open Door Policy',
			description:
				'Our leadership team is always accessible to members for feedback, suggestions, or concerns.',
			icon: '🚪'
		},
		{
			title: 'Continuous Learning',
			description:
				'We invest in ongoing education for our team to stay current with fitness science and trends.',
			icon: '📚'
		},
		{
			title: 'Member-First Mindset',
			description:
				'Every decision we make is evaluated through the lens of member benefit and experience.',
			icon: '👥'
		},
		{
			title: 'Environmental Responsibility',
			description:
				'We are committed to sustainable practices and reducing our environmental footprint.',
			icon: '🌱'
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
				<span class="text-sm font-medium text-white/70">⭐ What Drives Us</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				OUR CORE
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					VALUES
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				These values aren't just words on a wall - they're the foundation of everything we do and
				the principles that guide our decisions every day.
			</p>
		</div>

		<!-- Core Values Grid -->
		<div
			class="mb-20 grid transform grid-cols-1 gap-8 transition-all delay-400 duration-1000 md:grid-cols-2 lg:grid-cols-3 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each coreValues as value, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<!-- Background Gradient -->
					<div
						class="absolute inset-0 bg-gradient-to-br {value.color} opacity-5 transition-opacity duration-300 group-hover:opacity-10"
					></div>

					<!-- Content -->
					<div class="relative z-10">
						<!-- Icon -->
						<div class="mb-6 text-5xl">{value.icon}</div>

						<!-- Title -->
						<h3
							class="mb-4 text-2xl font-bold text-white transition-colors group-hover:text-gray-200"
						>
							{value.title}
						</h3>

						<!-- Description -->
						<p class="mb-6 leading-relaxed text-gray-300">
							{value.description}
						</p>

						<!-- Principles -->
						<div class="space-y-3">
							<h4 class="text-sm font-semibold tracking-wide text-white uppercase">
								How we live this:
							</h4>
							<ul class="space-y-2">
								{#each value.principles as principle}
									<li class="flex items-start space-x-2">
										<div class="mt-2 h-1 w-1 rounded-full bg-white/60"></div>
										<span class="text-sm text-gray-400">{principle}</span>
									</li>
								{/each}
							</ul>
						</div>
					</div>
				</div>
			{/each}
		</div>

		<!-- Culture & Environment -->
		<div
			class="mb-20 transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mb-12 text-center">
				<h3 class="mb-4 text-3xl font-bold text-white">Our Culture</h3>
				<p class="mx-auto max-w-2xl text-lg text-gray-300">
					Values come alive through culture. Here's how we create an environment where everyone can
					thrive.
				</p>
			</div>

			<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4">
				{#each culturalAspects as aspect, index}
					<div
						class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
						style="transition-delay: {index * 100}ms"
					>
						<div class="mb-4 text-3xl">{aspect.icon}</div>
						<h4 class="mb-3 text-lg font-bold text-white">{aspect.title}</h4>
						<p class="text-sm leading-relaxed text-gray-300">{aspect.description}</p>
					</div>
				{/each}
			</div>
		</div>

		<!-- Values in Action -->
		<div
			class="mb-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-5xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md md:p-12"
			>
				<h3 class="mb-8 text-center text-3xl font-bold text-white">Values in Action</h3>
				<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
					<!-- Left Column -->
					<div class="space-y-6">
						<div class="rounded-xl border border-green-500/20 bg-green-500/10 p-6">
							<h4 class="mb-3 text-lg font-bold text-green-400">Community Impact</h4>
							<p class="text-gray-300">
								We've donated over $50,000 to local charities and organized 25+ community fitness
								events, proving our commitment extends beyond our walls.
							</p>
						</div>

						<div class="rounded-xl border border-blue-500/20 bg-blue-500/10 p-6">
							<h4 class="mb-3 text-lg font-bold text-blue-400">Member Success</h4>
							<p class="text-gray-300">
								With a 98% member satisfaction rate and countless transformation stories, our values
								translate into real results for real people.
							</p>
						</div>
					</div>

					<!-- Right Column -->
					<div class="space-y-6">
						<div class="rounded-xl border border-purple-500/20 bg-purple-500/10 p-6">
							<h4 class="mb-3 text-lg font-bold text-purple-400">Innovation Leadership</h4>
							<p class="text-gray-300">
								We were the first gym in the city to integrate AI-powered workout tracking and
								virtual reality fitness experiences.
							</p>
						</div>

						<div class="rounded-xl border border-yellow-500/20 bg-yellow-500/10 p-6">
							<h4 class="mb-3 text-lg font-bold text-yellow-400">Team Excellence</h4>
							<p class="text-gray-300">
								Our team holds over 200 professional certifications and maintains the highest
								standards in the industry through continuous education.
							</p>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Member Testimonial -->
		<div
			class="transform transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/20 bg-gradient-to-r from-white/10 to-white/5 p-8 text-center backdrop-blur-md md:p-12"
			>
				<div class="mb-6 text-5xl">💬</div>
				<blockquote class="mb-6 text-2xl leading-relaxed text-white italic">
					"Power House isn't just a gym - it's a family. The values they talk about aren't just
					marketing; you feel them every day. From the way staff greets you to how members support
					each other, everything reflects their commitment to excellence and community."
				</blockquote>
				<div class="flex items-center justify-center space-x-4">
					<img
						src="https://images.unsplash.com/photo-1494790108755-2616b612b34c?ixlib=rb-4.0.3&auto=format&fit=crop&w=100&q=80"
						alt="Jennifer K."
						class="h-16 w-16 rounded-full object-cover"
					/>
					<div class="text-left">
						<div class="font-semibold text-white">Jennifer K.</div>
						<div class="text-sm text-gray-400">3-year member</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Call to Experience -->
		<div
			class="mt-16 transform text-center transition-all delay-1200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div class="mx-auto max-w-2xl">
				<h4 class="mb-4 text-2xl font-bold text-white">Experience Our Values</h4>
				<p class="mb-6 text-gray-300">
					Values are best experienced, not just read about. Come see how our principles create an
					environment where you can thrive.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row sm:justify-center">
					<button
						class="rounded-xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Schedule a Tour
					</button>
					<button
						class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
					>
						Meet Our Team
					</button>
				</div>
			</div>
		</div>
	</div>
</section>
