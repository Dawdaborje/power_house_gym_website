<script lang="ts">
	import { onMount } from 'svelte';

	let isVisible = false;

	interface SocialPost {
		id: string;
		author: string;
		avatar: string;
		timestamp: string;
		content: string;
		image?: string;
		likes: number;
		comments: number;
		type: 'achievement' | 'workout' | 'motivation' | 'event';
		tags: string[];
	}

	const socialPosts: SocialPost[] = [
		{
			id: 'post-1',
			author: 'Sarah Martinez',
			avatar:
				'https://images.unsplash.com/photo-1494790108755-2616b612b34c?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&q=80',
			timestamp: '2 hours ago',
			content:
				'Just hit a new deadlift PR of 315lbs! 🔥 The community support here is incredible - thank you everyone for cheering me on! Next goal: 350lbs 💪',
			image:
				'https://images.unsplash.com/photo-1583500178690-f7eb6bdecf5c?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			likes: 47,
			comments: 12,
			type: 'achievement',
			tags: ['PersonalRecord', 'Deadlift', 'StrengthTraining']
		},
		{
			id: 'post-2',
			author: 'Mike Johnson',
			avatar:
				'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&q=80',
			timestamp: '4 hours ago',
			content:
				"Morning HIIT session with the crew! Nothing beats starting the day with an amazing workout and even better people. See you all at tomorrow's challenge! 🚀",
			image:
				'https://images.unsplash.com/photo-1571902943202-507ec2618e8f?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			likes: 34,
			comments: 8,
			type: 'workout',
			tags: ['HIIT', 'MorningWorkout', 'TeamWork']
		},
		{
			id: 'post-3',
			author: 'Lisa Chen',
			avatar:
				'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&q=80',
			timestamp: '6 hours ago',
			content:
				"Remember: Progress isn't always linear. Some days you'll feel unstoppable, others you'll just show up. Both are victories. Keep going! ✨",
			likes: 89,
			comments: 15,
			type: 'motivation',
			tags: ['Motivation', 'Mindset', 'Progress']
		},
		{
			id: 'post-4',
			author: 'James Wilson',
			avatar:
				'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&q=80',
			timestamp: '8 hours ago',
			content:
				"Who's ready for tonight's Member Mixer? 🎉 Great way to meet new workout buddies and share fitness tips. Plus, healthy snacks! See you at 7 PM in the lounge.",
			likes: 23,
			comments: 6,
			type: 'event',
			tags: ['MemberMixer', 'Community', 'Networking']
		},
		{
			id: 'post-5',
			author: 'Emma Rodriguez',
			avatar:
				'https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&q=80',
			timestamp: '12 hours ago',
			content:
				'Yoga flow this morning was exactly what my soul needed. Grateful for this peaceful space and the amazing instructor Emma Wilson! 🧘‍♀️ Namaste.',
			image:
				'https://images.unsplash.com/photo-1506629905607-c7a4e6d05e4c?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80',
			likes: 56,
			comments: 9,
			type: 'workout',
			tags: ['Yoga', 'Mindfulness', 'SelfCare']
		},
		{
			id: 'post-6',
			author: 'David Kim',
			avatar:
				'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&q=80',
			timestamp: '1 day ago',
			content:
				"Consistency is key! Today marks my 100th consecutive day at Power House. Feeling stronger, healthier, and more confident than ever. Here's to the next 100! 🎯",
			likes: 127,
			comments: 23,
			type: 'achievement',
			tags: ['Consistency', 'Milestone', 'Dedication']
		}
	];

	const postTypes = {
		achievement: { icon: '🏆', color: 'text-yellow-400', bgColor: 'bg-yellow-500/20' },
		workout: { icon: '💪', color: 'text-red-400', bgColor: 'bg-red-500/20' },
		motivation: { icon: '✨', color: 'text-purple-400', bgColor: 'bg-purple-500/20' },
		event: { icon: '🎉', color: 'text-blue-400', bgColor: 'bg-blue-500/20' }
	};

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function formatTime(timestamp: string): string {
		return timestamp;
	}
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
				<span class="text-sm font-medium text-white/70">📱 Stay Connected</span>
			</div>
			<h2 class="mb-6 text-4xl font-black text-white md:text-5xl lg:text-6xl">
				COMMUNITY
				<span
					class="bg-gradient-to-r from-gray-200 via-white to-gray-300 bg-clip-text text-transparent"
				>
					FEED
				</span>
			</h2>
			<p class="mx-auto max-w-3xl text-xl text-gray-300">
				See what our amazing community is up to! Share your victories, motivate others, and stay
				connected with your Power House family.
			</p>
		</div>

		<div class="grid grid-cols-1 gap-12 lg:grid-cols-3">
			<!-- Social Feed -->
			<div class="lg:col-span-2">
				<div
					class="transform transition-all delay-400 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-8 opacity-0'}"
				>
					<!-- Create Post -->
					<div class="mb-8 rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
						<div class="flex items-center space-x-4">
							<div class="h-12 w-12 rounded-full border-2 border-white/30 bg-white/20"></div>
							<div class="flex-1">
								<input
									type="text"
									placeholder="Share your fitness journey..."
									class="w-full rounded-xl border border-gray-600 bg-gray-800 px-4 py-3 text-white placeholder-gray-400 focus:border-white focus:ring-2 focus:ring-white/20 focus:outline-none"
								/>
							</div>
							<button
								class="rounded-xl bg-white px-6 py-3 text-sm font-bold text-black transition-colors duration-300 hover:bg-gray-200"
							>
								Post
							</button>
						</div>
					</div>

					<!-- Posts -->
					<div class="space-y-6">
						{#each socialPosts as post, index}
							<div
								class="group rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md transition-all duration-300 hover:border-white/20 hover:bg-white/10"
								style="transition-delay: {index * 100}ms"
							>
								<!-- Post Header -->
								<div class="mb-4 flex items-start justify-between">
									<div class="flex items-center space-x-3">
										<img
											src={post.avatar}
											alt={post.author}
											class="h-12 w-12 rounded-full object-cover"
										/>
										<div>
											<h4 class="font-semibold text-white">{post.author}</h4>
											<p class="text-sm text-gray-400">{formatTime(post.timestamp)}</p>
										</div>
									</div>
									<div class="flex items-center space-x-2">
										<span
											class="flex items-center space-x-1 rounded-full px-3 py-1 text-xs font-medium {postTypes[
												post.type
											].color} {postTypes[post.type].bgColor}"
										>
											<span>{postTypes[post.type].icon}</span>
											<span class="capitalize">{post.type}</span>
										</span>
										<button
											class="rounded-lg bg-white/10 p-2 text-white/70 transition-colors hover:bg-white/20 hover:text-white"
										>
											<svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
												<path
													stroke-linecap="round"
													stroke-linejoin="round"
													stroke-width="2"
													d="M5 12h.01M12 12h.01M19 12h.01"
												/>
											</svg>
										</button>
									</div>
								</div>

								<!-- Post Content -->
								<p class="mb-4 leading-relaxed text-gray-300">
									{post.content}
								</p>

								<!-- Post Image -->
								{#if post.image}
									<div class="mb-4 overflow-hidden rounded-2xl">
										<img
											src={post.image}
											alt="Post content"
											class="h-64 w-full object-cover transition-transform duration-300 group-hover:scale-105"
										/>
									</div>
								{/if}

								<!-- Tags -->
								{#if post.tags.length > 0}
									<div class="mb-4 flex flex-wrap gap-2">
										{#each post.tags as tag}
											<span
												class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-white/70"
											>
												#{tag}
											</span>
										{/each}
									</div>
								{/if}

								<!-- Post Actions -->
								<div class="flex items-center justify-between border-t border-white/10 pt-4">
									<div class="flex space-x-6">
										<button
											class="flex items-center space-x-2 text-gray-400 transition-colors hover:text-red-400"
										>
											<svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
												<path
													stroke-linecap="round"
													stroke-linejoin="round"
													stroke-width="2"
													d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
												/>
											</svg>
											<span class="text-sm font-medium">{post.likes}</span>
										</button>
										<button
											class="flex items-center space-x-2 text-gray-400 transition-colors hover:text-blue-400"
										>
											<svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
												<path
													stroke-linecap="round"
													stroke-linejoin="round"
													stroke-width="2"
													d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"
												/>
											</svg>
											<span class="text-sm font-medium">{post.comments}</span>
										</button>
										<button
											class="flex items-center space-x-2 text-gray-400 transition-colors hover:text-green-400"
										>
											<svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
												<path
													stroke-linecap="round"
													stroke-linejoin="round"
													stroke-width="2"
													d="M8.684 13.342C8.886 12.938 9 12.482 9 12c0-.482-.114-.938-.316-1.342m0 2.684a3 3 0 110-2.684m0 2.684l6.632 3.316m-6.632-6l6.632-3.316m0 0a3 3 0 105.367-2.684 3 3 0 00-5.367 2.684zm0 9.316a3 3 0 105.367 2.684 3 3 0 00-5.367-2.684z"
												/>
											</svg>
											<span class="text-sm font-medium">Share</span>
										</button>
									</div>
									<button
										class="rounded-lg bg-white/10 px-4 py-2 text-sm font-medium text-white transition-colors hover:bg-white/20"
									>
										View Thread
									</button>
								</div>
							</div>
						{/each}
					</div>

					<!-- Load More -->
					<div class="mt-8 text-center">
						<button
							class="rounded-xl border border-white/20 bg-white/10 px-8 py-4 text-lg font-bold text-white transition-all duration-300 hover:bg-white hover:text-black"
						>
							Load More Posts
						</button>
					</div>
				</div>
			</div>

			<!-- Sidebar -->
			<div class="space-y-8">
				<!-- Community Stats -->
				<div
					class="transform transition-all delay-600 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-8 opacity-0'}"
				>
					<div class="rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
						<h3 class="mb-6 text-xl font-bold text-white">Community Stats</h3>
						<div class="space-y-4">
							<div class="flex items-center justify-between">
								<span class="text-gray-300">Daily Posts</span>
								<span class="font-bold text-white">127</span>
							</div>
							<div class="flex items-center justify-between">
								<span class="text-gray-300">Active Members</span>
								<span class="font-bold text-white">2,156</span>
							</div>
							<div class="flex items-center justify-between">
								<span class="text-gray-300">Total Likes</span>
								<span class="font-bold text-white">45.2K</span>
							</div>
							<div class="flex items-center justify-between">
								<span class="text-gray-300">Success Stories</span>
								<span class="font-bold text-white">892</span>
							</div>
						</div>
					</div>
				</div>

				<!-- Trending Tags -->
				<div
					class="transform transition-all delay-700 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-8 opacity-0'}"
				>
					<div class="rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
						<h3 class="mb-6 text-xl font-bold text-white">Trending Tags</h3>
						<div class="flex flex-wrap gap-2">
							{#each ['PersonalRecord', 'MorningWorkout', 'StrengthTraining', 'Motivation', 'TeamWork', 'Consistency', 'HIIT', 'Yoga'] as tag}
								<span
									class="rounded-full bg-white/10 px-3 py-1 text-sm font-medium text-white/80 transition-colors hover:bg-white/20"
								>
									#{tag}
								</span>
							{/each}
						</div>
					</div>
				</div>

				<!-- Active Now -->
				<div
					class="transform transition-all delay-800 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-8 opacity-0'}"
				>
					<div class="rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
						<h3 class="mb-6 text-xl font-bold text-white">Active Now</h3>
						<div class="space-y-3">
							{#each [{ name: 'Sarah M.', activity: 'In HIIT class', avatar: 'https://images.unsplash.com/photo-1494790108755-2616b612b34c?ixlib=rb-4.0.3&auto=format&fit=crop&w=60&q=80' }, { name: 'Mike J.', activity: 'Weight training', avatar: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=60&q=80' }, { name: 'Lisa C.', activity: 'Yoga session', avatar: 'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&auto=format&fit=crop&w=60&q=80' }, { name: 'James W.', activity: 'Cardio zone', avatar: 'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&auto=format&fit=crop&w=60&q=80' }] as member}
								<div class="flex items-center space-x-3">
									<div class="relative">
										<img
											src={member.avatar}
											alt={member.name}
											class="h-8 w-8 rounded-full object-cover"
										/>
										<div
											class="absolute -top-1 -right-1 h-3 w-3 rounded-full border-2 border-black bg-green-400"
										></div>
									</div>
									<div>
										<p class="text-sm font-medium text-white">{member.name}</p>
										<p class="text-xs text-gray-400">{member.activity}</p>
									</div>
								</div>
							{/each}
						</div>
					</div>
				</div>

				<!-- Community Guidelines -->
				<div
					class="transform transition-all delay-900 duration-1000 {isVisible
						? 'translate-y-0 opacity-100'
						: 'translate-y-8 opacity-0'}"
				>
					<div class="rounded-3xl border border-white/10 bg-white/5 p-6 backdrop-blur-md">
						<h3 class="mb-4 text-xl font-bold text-white">Community Guidelines</h3>
						<ul class="space-y-2">
							<li class="flex items-start space-x-2">
								<div class="mt-2 h-1 w-1 rounded-full bg-white/60"></div>
								<span class="text-sm text-gray-300">Be respectful and supportive</span>
							</li>
							<li class="flex items-start space-x-2">
								<div class="mt-2 h-1 w-1 rounded-full bg-white/60"></div>
								<span class="text-sm text-gray-300">Celebrate everyone's journey</span>
							</li>
							<li class="flex items-start space-x-2">
								<div class="mt-2 h-1 w-1 rounded-full bg-white/60"></div>
								<span class="text-sm text-gray-300">Share knowledge and tips</span>
							</li>
							<li class="flex items-start space-x-2">
								<div class="mt-2 h-1 w-1 rounded-full bg-white/60"></div>
								<span class="text-sm text-gray-300">Keep content fitness-focused</span>
							</li>
						</ul>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>
