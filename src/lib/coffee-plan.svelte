<script lang="ts">
	interface Props {
		name: string;
		selectedPlan: (name: string) => void;
		selected: boolean;
	}

	let { name = 'Default Plan', selectedPlan, selected }: Props = $props();

	const handleSelectPlan = () => {
		selectedPlan(name);
	};
</script>

<div onclick={handleSelectPlan} class={['plan', selected && 'active-plan']}>
	<div class="description">
		<span class="title"> {name} </span>
	</div>
</div>

<style></style>
