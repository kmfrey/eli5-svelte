<script>
  import { createEventDispatcher } from 'svelte';
  export let searchTerm;
  const dispatch = createEventDispatcher();

</script>

<style>
  input {
    width:25%;
    margin: 2rem;
  }
</style>

<input bind:value={searchTerm} on:input={() => dispatch('search', {searchTerm})}>