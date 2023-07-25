<script>
    let name;
    let color;
    let age;

    const handleSubmit = () => {
        console.log(name, color, age);
    };
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="Name" bind:value={name} />
    <input type="text" placeholder="Color" bind:value={color}/>
    <input type="number" placeholder="Age" bind:value={age}/>
    <button>Add Person</button>
</form>

<style>
</style>
