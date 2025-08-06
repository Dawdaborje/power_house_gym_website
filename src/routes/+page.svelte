<script>
	// Hero and Core Sections
	import HomeHero from '$lib/components/pages/home/homeHero.svelte';
	import WhyPowerHouse from '$lib/components/pages/common/whyPowerHouse.svelte';

	// Program and Community Sections
	import WorkoutPrograms from '$lib/components/pages/home/workoutPrograms.svelte';
	import CommunitySection from '$lib/components/pages/common/communitySection.svelte';

	// Social Proof and App
	import Testimonials from '$lib/components/pages/common/testimonials.svelte';
	import AppPromotion from '$lib/components/pages/common/appPromotion.svelte';

	// Conversion
	import MembershipCTA from '$lib/components/pages/common/membershipCTA.svelte';
</script>

<!-- Hero Section -->
<HomeHero />

<!-- Why Choose Us -->
<WhyPowerHouse />

<!-- Workout Programs -->
<WorkoutPrograms />

<!-- Community Focus -->
<CommunitySection />

<!-- Member Testimonials -->
<Testimonials />

<!-- App Promotion -->
<AppPromotion />

<!-- Membership Call-to-Action -->
<MembershipCTA />
