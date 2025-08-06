<script lang="ts">
	const quickLinks = [
		{ name: 'Home', href: '/' },
		{ name: 'About Us', href: '/about' },
		{ name: 'Programs', href: '/programs' },
		{ name: 'Trainers', href: '/trainers' },
		{ name: 'Pricing', href: '/pricing' },
		{ name: 'Contact', href: '/contact' }
	];

	const programs = [
		{ name: 'Strength Training', href: '/programs/strength' },
		{ name: 'Cardio Workouts', href: '/programs/cardio' },
		{ name: 'HIIT Classes', href: '/programs/hiit' },
		{ name: 'Personal Training', href: '/programs/personal' },
		{ name: 'Group Classes', href: '/programs/group' },
		{ name: 'Nutrition Plans', href: '/programs/nutrition' }
	];

	const resources = [
		{ name: 'Member Portal', href: '/portal' },
		{ name: 'Class Schedule', href: '/schedule' },
		{ name: 'Fitness Blog', href: '/blog' },
		{ name: 'Success Stories', href: '/stories' },
		{ name: 'FAQ', href: '/faq' },
		{ name: 'Support', href: '/support' }
	];

	const socialLinks = [
		{
			name: 'Instagram',
			href: '#',
			icon: 'M12.017 0C5.396 0 .029 5.367.029 11.987c0 5.079 3.158 9.417 7.618 11.024-.105-.949-.199-2.403.041-3.439.219-.937 1.406-5.957 1.406-5.957s-.359-.219-.359-1.219c0-1.142.662-1.995 1.488-1.995.702 0 1.041.219 1.041.219s.359.359.359.359c.661 1.142 1.729 2.081 1.729 2.081s.72-.359 1.081-.719c-.199-.539-.4-1.079-.4-1.439 0-1.801 1.086-3.439 2.627-3.439 1.142 0 2.081.879 2.081 1.801 0 1.079-.699 2.401-1.621 3.737-.539.779-1.402 1.438-2.283 1.797.04.199.359.359.719.359 2.242 0 4.323-1.797 4.323-4.198C21.988 5.367 18.637.029 12.017.029z'
		},
		{
			name: 'Facebook',
			href: '#',
			icon: 'M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z'
		},
		{
			name: 'Twitter',
			href: '#',
			icon: 'M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z'
		},
		{
			name: 'YouTube',
			href: '#',
			icon: 'M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z'
		}
	];

	let email = '';

	function handleNewsletterSubmit(event: Event) {
		event.preventDefault();
		// Handle newsletter subscription
		console.log('Newsletter subscription:', email);
		email = '';
		// You would typically send this to your backend
	}
</script>

<footer class="bg-black text-white">
	<!-- Main Footer Content -->
	<div class="mx-auto max-w-7xl px-4 py-16 sm:px-6 lg:px-8">
		<div class="grid grid-cols-1 gap-12 lg:grid-cols-12">
			<!-- Company Info -->
			<div class="lg:col-span-4">
				<!-- Logo -->
				<div class="mb-8 flex items-center space-x-4">
					<div class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white">
						<span class="text-2xl font-black text-black">PH</span>
					</div>
					<div>
						<div class="text-2xl font-bold text-white">POWER HOUSE</div>
						<div class="text-sm text-gray-400">ELITE FITNESS</div>
					</div>
				</div>

				<p class="mb-8 text-lg leading-relaxed text-gray-300">
					Transform your body, elevate your mind, and join the elite community of Power House
					athletes. Where strength meets determination and champions are forged.
				</p>

				<!-- Contact Info -->
				<div class="space-y-4">
					<div class="flex items-center space-x-3">
						<svg
							class="h-5 w-5 text-gray-400"
							fill="none"
							stroke="currentColor"
							viewBox="0 0 24 24"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
							/>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
							/>
						</svg>
						<span class="text-gray-300">123 Fitness Street, Muscle City, MC 12345</span>
					</div>

					<div class="flex items-center space-x-3">
						<svg
							class="h-5 w-5 text-gray-400"
							fill="none"
							stroke="currentColor"
							viewBox="0 0 24 24"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
							/>
						</svg>
						<span class="text-gray-300">(555) 123-POWER</span>
					</div>

					<div class="flex items-center space-x-3">
						<svg
							class="h-5 w-5 text-gray-400"
							fill="none"
							stroke="currentColor"
							viewBox="0 0 24 24"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
							/>
						</svg>
						<span class="text-gray-300">info@powerhousegym.com</span>
					</div>
				</div>
			</div>

			<!-- Quick Links -->
			<div class="lg:col-span-2">
				<h3 class="mb-6 text-lg font-bold text-white">Quick Links</h3>
				<ul class="space-y-3">
					{#each quickLinks as link}
						<li>
							<a
								href={link.href}
								class="text-gray-300 transition-colors duration-300 hover:text-white"
							>
								{link.name}
							</a>
						</li>
					{/each}
				</ul>
			</div>

			<!-- Programs -->
			<div class="lg:col-span-2">
				<h3 class="mb-6 text-lg font-bold text-white">Programs</h3>
				<ul class="space-y-3">
					{#each programs as program}
						<li>
							<a
								href={program.href}
								class="text-gray-300 transition-colors duration-300 hover:text-white"
							>
								{program.name}
							</a>
						</li>
					{/each}
				</ul>
			</div>

			<!-- Resources -->
			<div class="lg:col-span-2">
				<h3 class="mb-6 text-lg font-bold text-white">Resources</h3>
				<ul class="space-y-3">
					{#each resources as resource}
						<li>
							<a
								href={resource.href}
								class="text-gray-300 transition-colors duration-300 hover:text-white"
							>
								{resource.name}
							</a>
						</li>
					{/each}
				</ul>
			</div>

			<!-- Newsletter -->
			<div class="lg:col-span-2">
				<h3 class="mb-6 text-lg font-bold text-white">Stay Strong</h3>
				<p class="mb-6 text-gray-300">
					Get fitness tips, workout plans, and exclusive offers delivered to your inbox.
				</p>

				<form on:submit={handleNewsletterSubmit} class="space-y-4">
					<div>
						<input
							type="email"
							bind:value={email}
							placeholder="Enter your email"
							required
							class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white placeholder-gray-400 focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
						/>
					</div>
					<button
						type="submit"
						class="w-full rounded-xl bg-white px-4 py-3 font-bold text-black transition-colors duration-300 hover:bg-gray-200"
					>
						Subscribe
					</button>
				</form>

				<!-- Social Links -->
				<div class="mt-8">
					<h4 class="mb-4 text-sm font-semibold tracking-wider text-gray-400 uppercase">
						Follow Us
					</h4>
					<div class="flex space-x-4">
						{#each socialLinks as social}
							<a
								href={social.href}
								class="flex h-10 w-10 items-center justify-center rounded-lg bg-gray-800 text-gray-400 transition-all duration-300 hover:bg-white hover:text-black"
								aria-label={social.name}
							>
								<svg class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
									<path d={social.icon} />
								</svg>
							</a>
						{/each}
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Gym Hours -->
	<div class="border-t border-gray-800">
		<div class="mx-auto max-w-7xl px-4 py-8 sm:px-6 lg:px-8">
			<div class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-4">
				<div class="text-center">
					<h4 class="mb-2 font-bold text-white">Monday - Friday</h4>
					<p class="text-gray-300">5:00 AM - 11:00 PM</p>
				</div>
				<div class="text-center">
					<h4 class="mb-2 font-bold text-white">Saturday</h4>
					<p class="text-gray-300">6:00 AM - 10:00 PM</p>
				</div>
				<div class="text-center">
					<h4 class="mb-2 font-bold text-white">Sunday</h4>
					<p class="text-gray-300">7:00 AM - 9:00 PM</p>
				</div>
				<div class="text-center">
					<h4 class="mb-2 font-bold text-white">Holidays</h4>
					<p class="text-gray-300">Check Schedule</p>
				</div>
			</div>
		</div>
	</div>

	<!-- Bottom Bar -->
	<div class="border-t border-gray-800">
		<div class="mx-auto max-w-7xl px-4 py-6 sm:px-6 lg:px-8">
			<div class="flex flex-col items-center justify-between space-y-4 md:flex-row md:space-y-0">
				<div class="text-center text-gray-400 md:text-left">
					<p>&copy; 2024 Power House Elite Fitness. All rights reserved.</p>
				</div>

				<div class="flex flex-wrap items-center justify-center space-x-6 text-sm">
					<a href="/privacy" class="text-gray-400 hover:text-white">Privacy Policy</a>
					<a href="/terms" class="text-gray-400 hover:text-white">Terms of Service</a>
					<a href="/cookies" class="text-gray-400 hover:text-white">Cookie Policy</a>
					<a href="/accessibility" class="text-gray-400 hover:text-white">Accessibility</a>
				</div>

				<div class="flex items-center space-x-2 text-gray-400">
					<span>Powered by</span>
					<span class="font-semibold text-white">💪 Strength</span>
				</div>
			</div>
		</div>
	</div>
</footer>

<style>
	/* Custom focus styles */
	input:focus {
		transform: translateY(-1px);
	}

	/* Smooth transitions for hover effects */
	a {
		transition: all 0.3s ease;
	}
</style>
