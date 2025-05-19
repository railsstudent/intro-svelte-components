<script lang="ts">
import CoffeePlan from './coffee-plan.svelte';
const plans = $state(['The Single', 'The Curious', 'The Addict', 'The Hacker']);
</script>

<div class="plans">
    {#each plans as plan(plan)}
        <CoffeePlan name={plan} />
    {/each}
</div> 
