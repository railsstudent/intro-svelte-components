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

	{#snippet selectedPlanIcons(name: string)}
		<div>
			{#if name.startsWith('The')}
				<Icon icon="ic:outline-coffee" width="48" height="48" />
				<Icon icon="ic:outline-coffee-maker" width="48" height="48" />
			{:else}
				<Icon icon="material-symbols:emoji-food-beverage-outline" width="48" height="48" />
				<Icon icon="material-symbols:fastfood-outline" width="48" height="48" />
			{/if}
		</div>
	{/snippet}

	{#each plans as plan (plan)}
		<CoffeePlan name={plan} {selectedPlan} selected={isSelected(plan)} 
			selectedPlanIcons={isSelected(plan) ? selectedPlanIcons : undefined } />
	{/each}
</div>
