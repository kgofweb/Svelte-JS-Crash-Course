<script>
   import { createEventDispatcher } from 'svelte';
   const dispatch = createEventDispatcher();

	export let name;
   export let points;

	// Conditions
	let showControls = false;

	// Inc & Dec
	const addPoint = () => (points += 1);
	const removePoint = () => (points -= 1);
   const toggleControls = () => (showControls = !showControls);
   
   // Delete player
   const onDelete = () => dispatch('removePlayer', name);
</script>

<div class="card">
   <h3>
      {name}
      <button class="btn btn-sm" on:click={toggleControls}>
         {#if showControls} - {:else} + {/if}
      </button>
      <!-- Delete btn -->
      <buttton class="btn btn-danger btn-sm" on:click={onDelete}>x</buttton>
   </h3>

   <p>Points: {points}</p>
   
   {#if showControls}
      <!-- Btn Inc & Dec -->
      <button class="btn" on:click={addPoint}>Plus +1</button>
      <button class="btn btn-dark" on:click={removePoint} >Minus -1</button>

      <!-- Input -->
      <input type="number" bind:value={points}>
   {/if}
</div>