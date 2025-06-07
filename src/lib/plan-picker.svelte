<script lang="ts">
	import CoffeePlan from './coffee-plan.svelte';
	import AddCoffeePlan from './add-coffee-plan.svelte';
	const plans = $state(['The Single', 'The Curious', 'The Addict', 'The Hacker']);

	let selectedCoffeePlan = $state('');
	const selectedPlan = (name: string) => (selectedCoffeePlan = name);
</script>

<div class="plans">
	<AddCoffeePlan addCoffeePlan={(plan) => plans.push(plan)}>
		{#snippet addPlanButton(hover: boolean)}
			Add Plan {hover ? '(+1)' : ''}
		{/snippet}	
	</AddCoffeePlan>
	{selectedCoffeePlan}
	{#each plans as plan (plan)}
		<CoffeePlan name={plan} {selectedPlan} selected={selectedCoffeePlan === plan} />
	{/each}
</div>
