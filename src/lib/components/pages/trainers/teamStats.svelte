<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	const stats = [
		{
			number: '12',
			label: 'Expert Trainers',
			description: 'Certified professionals with diverse expertise',
			icon: '👥'
		},
		{
			number: '50+',
			label: 'Certifications',
			description: 'Combined professional certifications across our team',
			icon: '🏆'
		},
		{
			number: '75+',
			label: 'Years Combined',
			description: 'Total experience across all our trainers',
			icon: '⭐'
		},
		{
			number: '2000+',
			label: 'Success Stories',
			description: 'Members transformed through our guidance',
			icon: '💪'
		},
		{
			number: '98%',
			label: 'Client Satisfaction',
			description: 'Members who would recommend our trainers',
			icon: '❤️'
		},
		{
			number: '15',
			label: 'Specialties',
			description: 'Different areas of fitness expertise covered',
			icon: '🎯'
		}
	];

	const achievements = [
		{
			title: 'National Champions',
			description: '3 trainers with national competition titles',
			icon: '🥇'
		},
		{
			title: 'Advanced Degrees',
			description: '8 trainers with exercise science degrees',
			icon: '🎓'
		},
		{
			title: 'Continuing Education',
			description: '500+ hours of annual training completed',
			icon: '📚'
		},
		{
			title: 'Multilingual Team',
			description: '7 languages spoken across our staff',
			icon: '🌍'
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
				<span class="text-sm font-medium text-white/70">📊 Team Excellence</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				BY THE
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					NUMBERS
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Our team's credentials, experience, and results speak for themselves. Here's what sets our
				trainers apart.
			</p>
		</div>

		<!-- Stats Grid -->
		<div
			class="mb-20 grid transform grid-cols-1 gap-8 transition-all delay-400 duration-1000 md:grid-cols-2 lg:grid-cols-3 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each stats as stat, index}
				<div
					class="group relative overflow-hidden rounded-3xl border border-white/10 bg-white/5 p-8 text-center backdrop-blur-md transition-all duration-500 hover:border-white/20 hover:bg-white/10"
					style="transition-delay: {index * 100}ms"
				>
					<!-- Icon -->
					<div class="mb-4 text-4xl">{stat.icon}</div>

					<!-- Number -->
					<div class="mb-2 text-5xl font-black text-white md:text-6xl">
						{stat.number}
					</div>

					<!-- Label -->
					<h3 class="mb-3 text-xl font-bold text-white transition-colors group-hover:text-gray-200">
						{stat.label}
					</h3>

					<!-- Description -->
					<p class="leading-relaxed text-gray-300">
						{stat.description}
					</p>

					<!-- Hover Overlay -->
					<div
						class="absolute inset-0 opacity-0 transition-opacity duration-300 group-hover:opacity-100"
					>
						<div
							class="absolute inset-0 bg-gradient-to-t from-white/5 via-transparent to-transparent"
						></div>
					</div>
				</div>
			{/each}
		</div>

		<!-- Team Achievements -->
		<div
			class="transform transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mx-auto max-w-4xl rounded-3xl border border-white/10 bg-white/5 p-8 backdrop-blur-md md:p-12"
			>
				<h3 class="mb-8 text-center text-3xl font-black text-white md:text-4xl">
					Team Achievements
				</h3>

				<div class="grid grid-cols-1 gap-6 md:grid-cols-2">
					{#each achievements as achievement, index}
						<div
							class="flex items-start space-x-4 rounded-2xl border border-white/10 bg-white/5 p-6 transition-all duration-300 hover:bg-white/10"
							style="transition-delay: {200 + index * 100}ms"
						>
							<!-- Icon -->
							<div class="flex-shrink-0 text-3xl">{achievement.icon}</div>

							<!-- Content -->
							<div>
								<h4 class="mb-2 text-lg font-bold text-white">{achievement.title}</h4>
								<p class="text-gray-300">{achievement.description}</p>
							</div>
						</div>
					{/each}
				</div>

				<!-- CTA -->
				<div class="mt-8 text-center">
					<p class="mb-6 text-xl text-gray-300">Ready to work with our world-class team?</p>
					<button
						class="rounded-2xl bg-white px-8 py-4 text-lg font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Schedule Your Consultation
					</button>
				</div>
			</div>
		</div>

		<!-- Credentials Banner -->
		<div
			class="mt-16 transform transition-all delay-800 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="flex flex-wrap items-center justify-center gap-8 rounded-2xl border border-white/10 bg-white/5 p-6 backdrop-blur-md"
			>
				<div class="flex items-center space-x-3">
					<div
						class="flex h-12 w-12 items-center justify-center rounded-full border-2 border-white/30"
					>
						<span class="font-bold text-white">NSCA</span>
					</div>
					<span class="font-medium text-white">NSCA Certified</span>
				</div>
				<div class="flex items-center space-x-3">
					<div
						class="flex h-12 w-12 items-center justify-center rounded-full border-2 border-white/30"
					>
						<span class="font-bold text-white">NASM</span>
					</div>
					<span class="font-medium text-white">NASM Certified</span>
				</div>
				<div class="flex items-center space-x-3">
					<div
						class="flex h-12 w-12 items-center justify-center rounded-full border-2 border-white/30"
					>
						<span class="font-bold text-white">ACSM</span>
					</div>
					<span class="font-medium text-white">ACSM Certified</span>
				</div>
				<div class="flex items-center space-x-3">
					<div
						class="flex h-12 w-12 items-center justify-center rounded-full border-2 border-white/30"
					>
						<span class="font-bold text-white">CPR</span>
					</div>
					<span class="font-medium text-white">CPR/AED Certified</span>
				</div>
			</div>
		</div>
	</div>
</section>
