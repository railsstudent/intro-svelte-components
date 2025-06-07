<script lang="ts">
	import type { Snippet } from 'svelte';

	interface Props {
		name: string;
		selectedPlan: (name: string) => void;
		selected: boolean;
		selectedPlanIcons?: Snippet;
		selectedPlanBeverageIcons?: Snippet;
	}

	let {
		name = 'Default Plan',
		selectedPlan,
		selected,
		selectedPlanIcons,
		selectedPlanBeverageIcons
	}: Props = $props();

	const handleSelectPlan = () => {
		selectedPlan(name);
	};
</script>

<!-- svelte-ignore a11y_click_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
<div onclick={handleSelectPlan} class={['plan', selected && 'active-plan']}>
	{@render selectedPlanIcons?.()}
	<div class="description">
		<span class="title"> {name} </span>
	</div>
	{@render selectedPlanBeverageIcons?.()}
</div>

<style></style>
