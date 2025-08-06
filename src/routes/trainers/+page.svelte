<script>
	// Hero and Core Sections
	import TrainersHero from '$lib/components/pages/trainers/trainersHero.svelte';
	import TrainerProfiles from '$lib/components/pages/trainers/trainerProfiles.svelte';

	// Additional Sections
	import TeamStats from '$lib/components/pages/trainers/teamStats.svelte';
	import TrainerSpecialties from '$lib/components/pages/trainers/trainerSpecialties.svelte';
	import TrainerBooking from '$lib/components/pages/trainers/trainerBooking.svelte';
	import TrainerTestimonials from '$lib/components/pages/trainers/trainerTestimonials.svelte';
</script>

<svelte:head>
	<title>Expert Trainers - Power House Elite Fitness</title>
	<meta
		name="description"
		content="Meet our certified fitness professionals at Power House Elite Fitness. Expert trainers with specialized knowledge to help you achieve your fitness goals."
	/>
</svelte:head>

<!-- Trainers Hero -->
<TrainersHero />

<!-- Trainer Profiles -->
<TrainerProfiles />

<!-- Team Statistics -->
<TeamStats />

<!-- Trainer Specialties -->
<TrainerSpecialties />

<!-- Trainer Testimonials -->
<TrainerTestimonials />

<!-- Trainer Booking -->
<TrainerBooking />
