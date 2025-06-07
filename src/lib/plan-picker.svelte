<script lang="ts">
	import Icon from "@iconify/svelte";

	import CoffeePlan from './coffee-plan.svelte';
	import AddCoffeePlan from './add-coffee-plan.svelte';
	const plans = $state(['The Single', 'The Curious', 'The Addict', 'The Hacker', 'Vibe Coder']);

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

	{#snippet selectedPlanIcons()}
		<div class="coffee">
			{#each ['ic:outline-coffee', 'ic:outline-coffee-maker'] as name (name)}
				<Icon icon={name} width="48" height="48" />
			{/each}	
		</div>
	{/snippet}

	{#snippet selectedPlanBeverageIcons()}
		<div class="beverage">
			{#each ['ic:outline-emoji-food-beverage', 'ic:outline-fastfood'] as name (name)}
				<Icon icon={name} width="42" height="42" color="blue" />
			{/each}
		</div>
	{/snippet}

	{#each plans as plan (plan)}
		{#if isSelected(plan)}
			<CoffeePlan name={plan} {selectedPlan} selected={isSelected(plan)} 
			selectedPlanBeverageIcons={!plan.startsWith('The') ? selectedPlanBeverageIcons : undefined}
			selectedPlanIcons={plan.startsWith('The') ? selectedPlanIcons : undefined} />
		{:else}
			<CoffeePlan name={plan} {selectedPlan} selected={isSelected(plan)} />
		{/if}
	{/each}
</div>

<style>
	.coffee {
		display: flex; 
		align-items: center;
	}

	.beverage {
		display: flex; 
		flex-direction: column; 
		padding: 0.25rem;
	}

</style>