<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import NavBar from '$lib/components/layout/navBar.svelte';
	import Footer from '$lib/components/layout/footer.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Power House Elite Fitness - Transform Your Body, Elevate Your Mind</title>
	<meta
		name="description"
		content="Join Power House Elite Fitness - Where champions are forged and limits are shattered. Premium equipment, expert trainers, supportive community. Start your transformation today."
	/>
	<meta
		name="keywords"
		content="gym, fitness, strength training, cardio, personal training, power house, elite fitness"
	/>
</svelte:head>

<NavBar />

<main>
	{@render children?.()}
</main>

<Footer />
