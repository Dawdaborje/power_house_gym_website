<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;
	let activeFilter = 'all';

	const filters = [
		{ id: 'all', name: 'All Programs', count: 15 },
		{ id: 'strength', name: 'Strength Training', count: 4 },
		{ id: 'cardio', name: 'Cardio & Conditioning', count: 3 },
		{ id: 'hiit', name: 'HIIT & Functional', count: 4 },
		{ id: 'recovery', name: 'Recovery & Wellness', count: 2 },
		{ id: 'personal', name: 'Personal Training', count: 2 }
	];

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function setActiveFilter(filterId: string) {
		activeFilter = filterId;
		// Dispatch event for other components to listen to
		window.dispatchEvent(new CustomEvent('programFilterChange', { detail: filterId }));
	}
</script>

<section class="bg-black py-16">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<!-- Section Header -->
		<div
			class="mb-12 transform text-center transition-all delay-200 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="mb-6 inline-flex items-center rounded-full border border-white/10 bg-white/5 px-6 py-2"
			>
				<span class="text-sm font-medium text-white/70">🎯 Find Your Program</span>
			</div>
			<h2 class="mb-4 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				FILTER BY
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					CATEGORY
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				Choose from our diverse range of programs tailored to every fitness goal and experience
				level.
			</p>
		</div>

		<!-- Filter Buttons -->
		<div
			class="flex transform flex-wrap justify-center gap-4 transition-all delay-400 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			{#each filters as filter, index}
				<button
					on:click={() => setActiveFilter(filter.id)}
					class="group relative overflow-hidden rounded-2xl border-2 px-6 py-4 text-lg font-bold transition-all duration-300 {activeFilter ===
					filter.id
						? 'border-white bg-white text-black shadow-lg shadow-white/25'
						: 'border-white/20 bg-white/5 text-white hover:border-white/40 hover:bg-white/10'}"
					style="transition-delay: {100 + index * 50}ms"
				>
					<span class="relative z-10 flex items-center space-x-3">
						<span>{filter.name}</span>
						<span
							class="rounded-full px-2 py-1 text-xs font-medium {activeFilter === filter.id
								? 'bg-black/20 text-black'
								: 'bg-white/20 text-white'}"
						>
							{filter.count}
						</span>
					</span>

					<!-- Hover Animation -->
					{#if activeFilter !== filter.id}
						<div
							class="absolute inset-0 translate-x-full transform bg-white transition-transform duration-300 group-hover:translate-x-0"
						></div>
						<span
							class="absolute inset-0 z-10 flex items-center justify-center text-lg font-bold text-black opacity-0 transition-opacity duration-300 group-hover:opacity-100"
						>
							<span class="flex items-center space-x-3">
								<span>{filter.name}</span>
								<span class="rounded-full bg-black/20 px-2 py-1 text-xs font-medium text-black">
									{filter.count}
								</span>
							</span>
						</span>
					{/if}
				</button>
			{/each}
		</div>

		<!-- Filter Info -->
		<div
			class="mt-12 transform text-center transition-all delay-600 duration-1000 {isVisible
				? 'translate-y-0 opacity-100'
				: 'translate-y-8 opacity-0'}"
		>
			<div
				class="inline-flex items-center space-x-4 rounded-2xl border border-white/10 bg-white/5 px-6 py-3 backdrop-blur-md"
			>
				<div class="flex items-center space-x-2">
					<div class="h-2 w-2 animate-pulse rounded-full bg-green-400"></div>
					<span class="text-sm font-medium text-white">Live Classes Available</span>
				</div>
				<div class="h-4 w-px bg-white/20"></div>
				<div class="flex items-center space-x-2">
					<svg class="h-4 w-4 text-white/70" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
						/>
					</svg>
					<span class="text-sm font-medium text-white">Updated Weekly</span>
				</div>
				<div class="h-4 w-px bg-white/20"></div>
				<div class="flex items-center space-x-2">
					<svg class="h-4 w-4 text-white/70" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 715.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 919.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"
						/>
					</svg>
					<span class="text-sm font-medium text-white">All Levels Welcome</span>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	@keyframes pulse {
		0%,
		100% {
			opacity: 1;
		}
		50% {
			opacity: 0.5;
		}
	}

	.animate-pulse {
		animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
	}
</style>
