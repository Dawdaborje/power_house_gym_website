<script>
	// Hero and Core Sections
	import CommunityHero from '$lib/components/pages/community/communityHero.svelte';
	import MemberStories from '$lib/components/pages/community/memberStories.svelte';

	// Additional Sections
	import EventsCalendar from '$lib/components/pages/community/eventsCalendar.svelte';
	import FitnessChallenges from '$lib/components/pages/community/fitnessChallenges.svelte';
	import SocialFeed from '$lib/components/pages/community/socialFeed.svelte';
	import CommunityValues from '$lib/components/pages/community/communityValues.svelte';
	import CommunityCTA from '$lib/components/pages/community/communityCTA.svelte';
</script>

<svelte:head>
	<title>Community - Power House Elite Fitness</title>
	<meta
		name="description"
		content="Join the Power House community - where fitness meets friendship. Connect with like-minded members, participate in challenges, and be part of something bigger."
	/>
</svelte:head>

<!-- Community Hero -->
<CommunityHero />

<!-- Member Stories -->
<MemberStories />

<!-- Community Values -->
<CommunityValues />

<!-- Events Calendar -->
<EventsCalendar />

<!-- Fitness Challenges -->
<FitnessChallenges />

<!-- Social Feed -->
<SocialFeed />

<!-- Community CTA -->
<CommunityCTA />
