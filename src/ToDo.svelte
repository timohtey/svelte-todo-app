<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  export let name = '';
  $: isDone = false;

  function deleteToDo() {
    dispatch('deleteToDo', {
      name,
    });
  }
</script>

<div class="toDoItem">
  <input class="center" type="checkbox" bind:checked={isDone} />
  <p class:strikeThrough={isDone}>{name}</p>
  <button class="center" on:click={deleteToDo}>Delete</button>
</div>

<style>
  .toDoItem {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .strikeThrough {
    text-decoration: line-through;
  }

  .center {
    align-self: center;
  }

  p {
    padding-left: 10px;
    padding-right: 10px;
  }

  @media (min-width: 640px) {
    .toDoItem {
      max-width: none;
    }
  }
</style>
