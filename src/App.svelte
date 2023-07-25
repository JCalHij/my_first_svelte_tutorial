<script>
  import Modal from "./Modal.svelte";
  import AddPersonForm from "./AddPersonForm.svelte";

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

  /**
   * 
   * @param {CustomEvent} e
   */
  const onNewPerson = (e) => {
    const {name, color, age} = e.detail;
    const person = {
      id: id,
      name: name,
      color: color,
      age: age,
    };
    people = [...people, person];

    id++;
    toggleModal();
  }

  let showModal = false;
  const toggleModal = () => {
    showModal = !showModal;
  };
</script>

<Modal isPromo={false} showModal={showModal} on:click={toggleModal}>
  <AddPersonForm on:addPerson={onNewPerson}/>
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
</main>
