<script>
  import Modal from "./Modal.svelte";

  let people = [
    {id: 1, name: "Javi", color: "red", age: 30},
    {id: 2, name: "Mimi", color: "turquoise", age: 29},
    {id: 3, name: "Noah", color: "white", age: 0},
  ];

  const onDeletePerson = (personId) => {
    people = people.filter((person) => {
      return person.id != personId;
    });
  };
  
  let id = 4;
  let newName = "";
  let newColor = "";
  let newAge = 0;

  const onNewPerson = () => {
    const person = {
      id: id,
      name: newName,
      color: newColor,
      age: newAge,
    };
    people = [...people, person];

    id++;
  }

  let showModal = false;
  const toggleModal = () => {
    showModal = !showModal;
  };
</script>

<Modal isPromo={false} showModal={showModal} on:click={toggleModal}>
  <h3>Add a New Person</h3>
  <form action="">
    <input type="text" placeholder="Name">
    <input type="text" placeholder="Color">
    <input type="number" placeholder="Age">
  </form>
</Modal>
<main>
  <button on:click={toggleModal}>Open Modal</button>
  {#if people.length < 5}
    <h1>Some People</h1>
  {:else if people.length < 8}
    <h1>Lots of People</h1>
  {:else}
    <h1>Infinite People</h1>
  {/if}

  {#each people as p (p.id)}
    <div style="color: {p.color}">
      <h4>{p.name} is {p.age} years old</h4>
      <button on:click={(e) => {onDeletePerson(p.id);}}>Delete Person</button>
    </div>
  {:else}
      <p>There is no one here...</p>
  {/each}

  <p>Name</p>
  <input type="text" bind:value={newName}>
  <br>
  <p>Color</p>
  <input type="text" bind:value={newColor}>
  <br>
  <p>Age</p>
  <input type="number" bind:value={newAge}>
  <br>
  <button on:click={onNewPerson}>Submit</button>
</main>
