<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	const achievements = [
		{
			year: '2024',
			title: 'Best Gym in the City',
			organization: 'City Fitness Awards',
			description: 'Voted #1 gym by local fitness enthusiasts for the third consecutive year.',
			icon: '🏆'
		},
		{
			year: '2023',
			title: 'Excellence in Member Experience',
			organization: 'International Fitness Association',
			description: 'Recognized for outstanding member satisfaction and retention rates.',
			icon: '⭐'
		},
		{
			year: '2023',
			title: 'Innovation in Fitness Technology',
			organization: 'FitTech Awards',
			description:
				'First gym to integrate AI-powered workout tracking and virtual reality training.',
			icon: '🚀'
		},
		{
			year: '2022',
			title: 'Community Impact Award',
			organization: 'Chamber of Commerce',
			description: 'Honored for charitable contributions and community wellness programs.',
			icon: '🤝'
		},
		{
			year: '2022',
			title: 'Green Business Certification',
			organization: 'Environmental Council',
			description: 'Achieved certification for sustainable practices and energy efficiency.',
			icon: '🌱'
		},
		{
			year: '2021',
			title: 'Top Employer in Fitness',
			organization: 'Employment Excellence Board',
			description: 'Recognized for exceptional employee satisfaction and development programs.',
			icon: '👥'
		}
	];

	const milestones = [
		{ number: '15,000+', label: 'Lives Transformed', icon: '💪' },
		{ number: '98%', label: 'Member Satisfaction', icon: '😊' },
		{ number: '50+', label: 'Industry Certifications', icon: '📜' },
		{ number: '25+', label: 'Community Events Hosted', icon: '🎉' },
		{ number: '$50K+', label: 'Donated to Charity', icon: '❤️' },
		{ number: '200+', label: 'Team Certifications', icon: '🎓' }
	];

	const industryRecognition = [
		{
			metric: 'Member Retention Rate',
			value: '94%',
			industry: '67%',
			description: 'Significantly above industry average'
		},
		{
			metric: 'Safety Record',
			value: '0.001%',
			industry: '0.5%',
			description: 'Injury rate per member visit'
		},
		{
			metric: 'Equipment Uptime',
			value: '99.8%',
			industry: '92%',
			description: 'Operational availability'
		},
		{
			metric: 'Member Satisfaction',
			value: '4.9/5',
			industry: '3.8/5',
			description: 'Average rating'
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
				<span class="text-sm font-medium text-white/70">🏆 Recognition & Excellence</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				ACHIEVEMENTS &
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					RECOGNITION
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Our commitment to excellence has been recognized by industry leaders, community
				organizations, and most importantly, our members.
			</p>
		</div>

		<!-- Key Milestones -->
		<div
			class="mb-20 grid transform grid-cols-2 gap-6 transition-all delay-400 duration-1000 md:grid-cols-3 lg:grid-cols-6 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each milestones as milestone, index}
				<div
					class="rounded-2xl border border-white/10 bg-white/5 p-6 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<div class="mb-3 text-3xl">{milestone.icon}</div>
					<div class="mb-2 text-2xl font-bold text-white">{milestone.number}</div>
					<div class="text-sm text-gray-400">{milestone.label}</div>
				</div>
			{/each}
		</div>

		<!-- Awards & Recognition -->
		<div
			class="mb-20 transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Awards & Recognition</h3>
			<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-3">
				{#each achievements as achievement, index}
					<div
						class="group rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10"
						style="transition-delay: {index * 150}ms"
					>
						<div class="mb-6 text-center">
							<div class="mb-4 text-5xl">{achievement.icon}</div>
							<div class="mb-2 rounded-full bg-white/10 px-3 py-1">
								<span class="text-sm font-medium text-white">{achievement.year}</span>
							</div>
						</div>

						<h4
							class="mb-3 text-xl font-bold text-white transition-colors group-hover:text-gray-200"
						>
							{achievement.title}
						</h4>

						<p class="mb-4 text-sm font-medium text-gray-400">{achievement.organization}</p>

						<p class="leading-relaxed text-gray-300">{achievement.description}</p>
					</div>
				{/each}
			</div>
		</div>

		<!-- Industry Benchmarks -->
		<div
			class="mb-20 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Industry Leadership</h3>
			<div
				class="mx-auto max-w-5xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md md:p-12"
			>
				<p class="mb-8 text-center text-lg text-gray-300">
					Our performance metrics consistently exceed industry standards, demonstrating our
					commitment to excellence in every aspect of our operations.
				</p>

				<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
					{#each industryRecognition as metric, index}
						<div
							class="rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md"
							style="transition-delay: {index * 100}ms"
						>
							<h4 class="mb-4 text-lg font-bold text-white">{metric.metric}</h4>

							<div class="mb-4 flex items-end space-x-4">
								<div class="text-center">
									<div class="text-sm text-gray-400">Power House</div>
									<div class="text-3xl font-bold text-green-400">{metric.value}</div>
								</div>
								<div class="text-center">
									<div class="text-sm text-gray-400">Industry Avg</div>
									<div class="text-xl font-semibold text-gray-500">{metric.industry}</div>
								</div>
							</div>

							<p class="text-sm text-gray-400">{metric.description}</p>
						</div>
					{/each}
				</div>
			</div>
		</div>

		<!-- Certifications & Partnerships -->
		<div
			class="mb-20 transform transition-all delay-1000 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<h3 class="mb-12 text-center text-3xl font-bold text-white">Certifications & Partnerships</h3>
			<div class="grid grid-cols-2 gap-6 md:grid-cols-4 lg:grid-cols-6">
				{#each [{ name: 'NSCA', title: 'National Strength & Conditioning Association', logo: '🏋️‍♂️' }, { name: 'ACSM', title: 'American College of Sports Medicine', logo: '🏥' }, { name: 'NASM', title: 'National Academy of Sports Medicine', logo: '🎓' }, { name: 'IHRSA', title: 'International Health & Fitness Association', logo: '🌍' }, { name: 'Green Business', title: 'Certified Green Business', logo: '🌱' }, { name: 'Safety First', title: 'OSHA Safety Certified', logo: '🛡️' }] as cert, index}
					<div
						class="rounded-xl border border-white/10 bg-white/5 p-4 text-center backdrop-blur-md transition-all duration-300 hover:bg-white/10"
						style="transition-delay: {index * 100}ms"
					>
						<div class="mb-2 text-2xl">{cert.logo}</div>
						<div class="mb-1 text-sm font-bold text-white">{cert.name}</div>
						<div class="text-xs text-gray-400">{cert.title}</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- Future Goals -->
		<div
			class="transform transition-all delay-1200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md"
			>
				<h3 class="mb-6 text-3xl font-bold text-white">Our Commitment to Excellence</h3>
				<p class="mb-8 text-lg leading-relaxed text-gray-300">
					These achievements represent more than awards on our wall - they reflect our unwavering
					commitment to providing exceptional experiences for our members and making a positive
					impact in our community. As we continue to grow, we remain dedicated to setting new
					standards of excellence in the fitness industry.
				</p>

				<div class="grid grid-cols-1 gap-6 md:grid-cols-3">
					<div class="rounded-xl border border-blue-500/20 bg-blue-500/10 p-4">
						<div class="mb-2 text-3xl">🎯</div>
						<div class="font-semibold text-white">Continuous Improvement</div>
						<div class="text-sm text-gray-400">Always raising the bar higher</div>
					</div>
					<div class="rounded-xl border border-green-500/20 bg-green-500/10 p-4">
						<div class="mb-2 text-3xl">🌟</div>
						<div class="font-semibold text-white">Member-Focused Innovation</div>
						<div class="text-sm text-gray-400">Your success drives our innovation</div>
					</div>
					<div class="rounded-xl border border-purple-500/20 bg-purple-500/10 p-4">
						<div class="mb-2 text-3xl">🚀</div>
						<div class="font-semibold text-white">Industry Leadership</div>
						<div class="text-sm text-gray-400">Setting tomorrow's standards today</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>
