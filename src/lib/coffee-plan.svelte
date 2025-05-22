<script lang="ts">
	let { name = 'Default Plan', selectedPlan, selected } = $props();
	
	const handleSelectPlan = () => {
		selectedPlan(name)
	}
</script>

<div onclick={handleSelectPlan} class={['plan', selected && 'active-plan']}>
	<div class="description">
		<span class="title"> {name} </span>
	</div>
</div>

<style></style>
