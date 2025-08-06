<script>
	// Hero and Core Sections
	import AboutHero from '$lib/components/pages/about/aboutHero.svelte';
	import AboutStory from '$lib/components/pages/about/aboutStory.svelte';

	// Additional Sections
	import AboutValues from '$lib/components/pages/about/aboutValues.svelte';
	import AboutTeam from '$lib/components/pages/about/aboutTeam.svelte';
	import AboutFacilities from '$lib/components/pages/about/aboutFacilities.svelte';
	import AboutAchievements from '$lib/components/pages/about/aboutAchievements.svelte';
	import AboutCommunity from '$lib/components/pages/about/aboutCommunity.svelte';
	import AboutCTA from '$lib/components/pages/about/aboutCTA.svelte';
</script>

<svelte:head>
	<title>About Us - Power House Elite Fitness</title>
	<meta
		name="description"
		content="Learn about Power House Elite Fitness - our story, mission, values, and the passionate team dedicated to helping you achieve your fitness goals."
	/>
</svelte:head>

<!-- About Hero -->
<AboutHero />

<!-- Our Story -->
<AboutStory />

<!-- Our Values -->
<AboutValues />

<!-- Leadership Team -->
<AboutTeam />

<!-- Facilities -->
<AboutFacilities />

<!-- Achievements -->
<AboutAchievements />

<!-- Community Impact -->
<AboutCommunity />

<!-- About CTA -->
<AboutCTA />
