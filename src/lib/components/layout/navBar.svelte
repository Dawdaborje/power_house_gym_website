<script lang="ts">
	import { onMount } from 'svelte';
	import { page } from '$app/stores';

	let scrolled = false;
	let mobileMenuOpen = false;

	const navItems = [
		{ name: 'Home', href: '/' },
		{ name: 'Programs', href: '/programs' },
		{ name: 'Trainers', href: '/trainers' },
		{ name: 'Community', href: '/community' },
		{ name: 'Pricing', href: '/pricing' },
		{ name: 'About', href: '/about' }
	];

	// Function to check if a nav item is active
	function isActive(href: string, currentPath: string) {
		if (href === '/') {
			return currentPath === '/';
		}
		return currentPath.startsWith(href);
	}

	onMount(() => {
		const handleScroll = () => {
			scrolled = window.scrollY > 50;
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function toggleMobileMenu() {
		mobileMenuOpen = !mobileMenuOpen;
	}

	function closeMobileMenu() {
		mobileMenuOpen = false;
	}
</script>

<nav
	class="fixed top-0 z-50 w-full transition-all duration-300 {scrolled
		? 'bg-black shadow-2xl'
		: 'bg-black/90 backdrop-blur-md'}"
>
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="flex h-20 items-center justify-between">
			<!-- Logo -->
			<div class="flex items-center space-x-4">
				<div class="flex h-12 w-12 items-center justify-center rounded-xl bg-white">
					<span class="text-lg font-black text-black">PH</span>
				</div>
				<div class="hidden sm:block">
					<div class="text-lg font-bold text-white">POWER HOUSE</div>
					<div class="text-xs text-gray-300">ELITE FITNESS</div>
				</div>
			</div>

			<!-- Desktop Navigation -->
			<div class="hidden lg:flex lg:items-center lg:space-x-8">
				{#each navItems as item}
					<a
						href={item.href}
						class="relative px-3 py-2 text-sm font-semibold transition-colors duration-300 {isActive(
							item.href,
							$page.url.pathname
						)
							? 'text-white'
							: 'text-gray-300 hover:text-white'}"
					>
						{item.name}
						{#if isActive(item.href, $page.url.pathname)}
							<div
								class="absolute bottom-0 left-0 h-0.5 w-full bg-gradient-to-r from-white to-gray-300"
							></div>
						{/if}
					</a>
				{/each}
			</div>

			<!-- Desktop CTA Buttons -->
			<div class="hidden lg:flex lg:items-center lg:space-x-4">
				<button
					class="rounded-xl border border-white/20 bg-white/10 px-6 py-3 text-sm font-semibold text-white backdrop-blur-md transition-all duration-300 hover:bg-white/20"
				>
					Free Trial
				</button>
				<button
					class="rounded-xl bg-white px-6 py-3 text-sm font-bold text-black transition-all duration-300 hover:bg-gray-200"
				>
					Join Now
				</button>
			</div>

			<!-- Mobile Menu Button -->
			<button
				class="rounded-lg p-2 text-white transition-colors duration-300 hover:bg-white/10 lg:hidden"
				on:click={toggleMobileMenu}
				aria-label="Toggle mobile menu"
			>
				<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					{#if mobileMenuOpen}
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					{:else}
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						/>
					{/if}
				</svg>
			</button>
		</div>
	</div>

	<!-- Mobile Menu -->
	<div
		class="overflow-hidden transition-all duration-300 lg:hidden {mobileMenuOpen
			? 'max-h-96 opacity-100'
			: 'max-h-0 opacity-0'}"
	>
		<div class="border-t border-white/10 bg-black/95 backdrop-blur-md">
			<div class="space-y-4 px-4 py-6">
				<!-- Mobile Navigation Links -->
				{#each navItems as item}
					<a
						href={item.href}
						class="block px-4 py-3 text-lg font-semibold transition-colors duration-300 {isActive(
							item.href,
							$page.url.pathname
						)
							? 'rounded-xl bg-white/10 text-white'
							: 'rounded-xl text-gray-300 hover:bg-white/5 hover:text-white'}"
						on:click={closeMobileMenu}
					>
						{item.name}
					</a>
				{/each}

				<!-- Mobile CTA Buttons -->
				<div class="space-y-3 border-t border-white/10 pt-4">
					<button
						class="w-full rounded-xl border border-white/20 bg-white/10 px-6 py-4 text-lg font-semibold text-white backdrop-blur-md transition-all duration-300 hover:bg-white/20"
					>
						Start Free Trial
					</button>
					<button
						class="w-full rounded-xl bg-white px-6 py-4 text-lg font-bold text-black transition-all duration-300 hover:bg-gray-200"
					>
						Join Power House
					</button>
				</div>

				<!-- Mobile Contact Info -->
				<div class="border-t border-white/10 pt-4">
					<div class="flex items-center space-x-4 text-gray-300">
						<div class="flex items-center space-x-2">
							<svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
								/>
							</svg>
							<span class="text-sm">(555) 123-4567</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</nav>

<!-- Navbar Spacer (to prevent content from hiding behind fixed navbar) -->
<div class="h-20"></div>

<style>
	/* Smooth transitions for mobile menu */
	.max-h-0 {
		max-height: 0;
	}
	.max-h-96 {
		max-height: 24rem;
	}
</style>
