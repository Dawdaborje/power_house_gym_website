<script>
	// Hero and Core Sections
	import PricingHero from '$lib/components/pages/pricing/pricingHero.svelte';
	import PricingPlans from '$lib/components/pages/pricing/pricingPlans.svelte';

	// Additional Sections
	import PricingComparison from '$lib/components/pages/pricing/pricingComparison.svelte';
	import PricingAddons from '$lib/components/pages/pricing/pricingAddons.svelte';
	import PricingFAQ from '$lib/components/pages/pricing/pricingFAQ.svelte';
	import PricingCorporate from '$lib/components/pages/pricing/pricingCorporate.svelte';
	import PricingCTA from '$lib/components/pages/pricing/pricingCTA.svelte';
</script>

<svelte:head>
	<title>Pricing - Power House Elite Fitness</title>
	<meta
		name="description"
		content="Choose the perfect membership plan at Power House Elite Fitness. Flexible pricing options, premium features, and unbeatable value for your fitness journey."
	/>
</svelte:head>

<!-- Pricing Hero -->
<PricingHero />

<!-- Pricing Plans -->
<PricingPlans />

<!-- Features Comparison -->
<PricingComparison />

<!-- Add-ons & Services -->
<PricingAddons />

<!-- Corporate Plans -->
<PricingCorporate />

<!-- FAQ Section -->
<PricingFAQ />

<!-- Pricing CTA -->
<PricingCTA />
