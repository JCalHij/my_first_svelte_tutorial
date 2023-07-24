<script>
  let name = "Javi";
  let inputName = "";

  const handleClick = () => {
    name = inputName;
  }

  const handleInput = (e) => {
    inputName = e.target.value;
  }
  
  let syncedValue = "Mimi";
  const handleSecondInput = (e) => {
    syncedValue = e.target.value;
  }

  let bindValue = "Hello";
</script>

<main>
  <h1>My title</h1>
  <p>Hello {name}</p>
  <input value={inputName} type="text" on:input={handleInput}>
  <button on:click={handleClick}>Update Name</button>
  <br>
  <br>
  <p>Sync value: {syncedValue}</p>
  <input value={syncedValue} type="text" on:input={handleSecondInput}>
  <button on:click={()=>{syncedValue = name;}}>Another button</button>
  <br>
  <br>
  <p>Sync value: {bindValue}</p>
  <input bind:value={bindValue} type="text">
</main>
