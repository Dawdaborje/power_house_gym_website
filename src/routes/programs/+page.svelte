<script>
	// Hero and Core Sections
	import ProgramsHero from '$lib/components/pages/programs/programsHero.svelte';
	import ProgramFilters from '$lib/components/pages/programs/programFilters.svelte';
	import ProgramCards from '$lib/components/pages/programs/programCards.svelte';

	// Additional Sections
	import ClassSchedule from '$lib/components/pages/programs/classSchedule.svelte';
	import TrainerShowcase from '$lib/components/pages/programs/trainerShowcase.svelte';
	import ProgramsCTA from '$lib/components/pages/programs/programsCTA.svelte';
</script>

<svelte:head>
	<title>Programs - Power House Elite Fitness</title>
	<meta
		name="description"
		content="Discover our comprehensive fitness programs at Power House Elite Fitness. From strength training to cardio, HIIT to personal training - find your perfect workout."
	/>
</svelte:head>

<!-- Programs Hero -->
<ProgramsHero />

<!-- Program Filters -->
<ProgramFilters />

<!-- Program Cards Grid -->
<ProgramCards />

<!-- Class Schedule -->
<ClassSchedule />

<!-- Featured Trainers -->
<TrainerShowcase />

<!-- Programs CTA -->
<ProgramsCTA />
