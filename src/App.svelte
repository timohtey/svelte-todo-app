<script>
  import ToDo from './ToDo.svelte';

  let name = '';
  $: toDos = [];

  function addToDo() {
    if (name) {
      toDos = [...toDos, name];
      name = '';
    }
  }

  function deleteToDo(event) {
    const toDoToBeDeleted = event.detail.name;
    toDos = toDos.filter((toDo) => toDo !== toDoToBeDeleted);
  }
</script>

<main>
  <h1>To-do List</h1>
  <form on:click|preventDefault={addToDo}>
    <input type="text" placeholder="Add To-Do" bind:value={name} />
    <button>Add</button>
  </form>
  {#each toDos as toDo}
    <ToDo name={toDo} on:deleteToDo={deleteToDo} />
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
