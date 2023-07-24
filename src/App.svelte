<script>
  let name = "Javi";
  const handleClick = () => {
    name = "Javixu";
  }
</script>

<main>
  <h1>My title</h1>
  <p>Hello {name}</p>
  <button on:click={handleClick}>Click me to change the name</button>
</main>
