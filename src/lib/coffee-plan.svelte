<script lang="ts">
	import type { Snippet } from 'svelte';

	interface Props {
		name: string;
		selectedPlan: (name: string) => void;
		selected: boolean;
		selectedPlanIcons?: Snippet<[string[]]>;
	}

	let { name = 'Default Plan', selectedPlan, selected, selectedPlanIcons }: Props = $props();

	const handleSelectPlan = () => {
		selectedPlan(name);
	};
	
	const iconsNames = $derived.by(() => {
		return name.startsWith('The')  ? ['ic:outline-coffee', 'ic:outline-coffee-maker'] : [
			'ic:outline-emoji-food-beverage', 'ic:outline-fastfood'
		];
	});
</script>

<!-- svelte-ignore a11y_click_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
<div onclick={handleSelectPlan} class={['plan', selected && 'active-plan']}>
	{@render selectedPlanIcons?.(iconsNames)}
	<div class="description">
		<span class="title"> {name} </span>
	</div>
</div>

<style></style>
