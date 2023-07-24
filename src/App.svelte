<script>
  const people = [
    {id: 1, name: "Javi", color: "red", age: 30},
    {id: 2, name: "Mimi", color: "turquoise", age: 29},
    {id: 3, name: "Noah", color: "white", age: 0},
  ];
</script>

<main>
  <h1>People</h1>
  {#each people as p (p.id)}
    <div style="color: {p.color}">
      <p>{p.name} is {p.age} years old</p>
    </div>
    {:else}
      <p>There is no one here...</p>
  {/each}
</main>
