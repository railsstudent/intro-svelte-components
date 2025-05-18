<script lang="ts">
	import CoffeePlan from '$lib/coffee-plan.svelte';

	const plans = $state(['The Single', 'The Curious', 'The Addict', 'The Hacker']);
</script>

<div class="content">
	<h1 class="title">Coffee Plans</h1>

	<h2 class="subtitle">We travel the world to source the very best single origin coffee for you</h2>

	<div class="plans">
		{#each plans as plan (plan)}
			<CoffeePlan name={plan} />
		{/each}
	</div>
</div>
