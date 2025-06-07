<script lang="ts">
	import Icon from "@iconify/svelte";

	import CoffeePlan from './coffee-plan.svelte';
	import AddCoffeePlan from './add-coffee-plan.svelte';
	const plans = $state(['The Single', 'The Curious', 'The Addict', 'The Hacker']);

	let selectedCoffeePlan = $state('');
	const selectedPlan = (name: string) => (selectedCoffeePlan = name);
	const isSelected = (plan: string) => selectedCoffeePlan === plan;
</script>

<div class="plans">
	<AddCoffeePlan addCoffeePlan={(plan) => plans.push(plan)}>
		{#snippet addPlanButton(hover: boolean)}
			Add Plan {hover ? '(+1)' : ''}
		{/snippet}	
	</AddCoffeePlan>
	{selectedCoffeePlan}

	{#snippet selectedPlanIcons(names: string[])}
		<div>
			{#each names as name (name)}
				<Icon icon={name} width="48" height="48" />
			{/each}
		</div>
	{/snippet}

	{#each plans as plan (plan)}
		<CoffeePlan name={plan} {selectedPlan} selected={isSelected(plan)} 
			selectedPlanIcons={isSelected(plan) ? selectedPlanIcons : undefined } />
	{/each}
</div>
