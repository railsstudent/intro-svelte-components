<script lang="ts">
	import PlanPicker from '$lib/plan-picker.svelte';

	const plans = $state(['The Single', 'The Curious', 'The Addict', 'The Hacker']);
</script>

<div class="content">
	<h1 class="title">Coffee Plans - Svelte 5</h1>

	<h2 class="subtitle">We travel the world to source the very best single origin coffee for you</h2>

	<PlanPicker />
</div>
