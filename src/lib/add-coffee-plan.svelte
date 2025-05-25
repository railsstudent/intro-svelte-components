<script lang="ts">
interface Props {
    addCoffeePlan: (plan: string) => void;
}

const { addCoffeePlan }: Props = $props();

let newPlan = $state('');
const addPlan = (e: SubmitEvent) => {
    e.preventDefault();
    const trimmedPlan = newPlan.trim();
    if (!trimmedPlan) {
        return;
    }
    
    addCoffeePlan(trimmedPlan);
    newPlan = '';
}
</script>

<form class="add-plan-form" onsubmit={addPlan}>
    <input type="text" placeholder="Add a new plan" bind:value={newPlan} />
    <button type="submit" class="btn btn-primary" disabled={newPlan.length < 5}>
        Add Plan
    </button>
</form>	

<style>
    input {
      padding: 0.5rem 0.75rem;
    }
    
    .add-plan-form {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    
    .add-plan-form input {
      width: 70%;
      border-radius: 3px;
      box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.1);
      border: 1px solid #f1f5f8;
      color: #606f7b;
      padding: 0.5rem 0.75rem;
      box-sizing: border-box;
      font-size: 1rem;
      letter-spacing: 0.5px;
      margin: 0.5rem 0;
    }
</style>
