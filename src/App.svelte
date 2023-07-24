<script>
  const title = "Bullshit";
  let firstName = "Javier";
  let lastName = "Calderon";
  let color = "white";
  let numClicks = 0;

  // Reactive variable
  $: fullName = `${firstName} ${lastName}`;
  // Reactive statement
  $: if (numClicks % 5 == 0) {
    fullName = fullName.toUpperCase();
  } else {
    fullName = `${firstName} ${lastName}`;
  }
</script>

<main>
  <h1>{title}</h1>
  <p style="color: {color}">{fullName} - {color}</p>
  <input type="text" bind:value={firstName}>
  <input type="text" bind:value={lastName}>
  <input bind:value={color}>
  <button on:click={() => {numClicks++;}}>Click Me!</button>
</main>
