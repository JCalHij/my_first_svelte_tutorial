<script>
    import { createEventDispatcher } from "svelte";

    let name;
    let color;
    let age;
    let isFighter = false;
    let isHider = false;
    let isFleer = false;

    let dispatch = createEventDispatcher();

    const handleSubmit = () => {
        const person = {
            name: name, 
            color: color, 
            age: age
        };
        dispatch("addPerson", person);
    };
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="Name" bind:value={name} />
    <input type="number" placeholder="Age" bind:value={age}/>
    <br>
    <label>Skills:</label>
    <input type="checkbox" bind:checked={isFighter}>Fighting<br>
    <input type="checkbox" bind:checked={isHider}>Hiding<br>
    <input type="checkbox" bind:checked={isFleer}>Fleeing<br>
    <br>
    <label>Colors:</label>
    <select bind:value={color}>
        <option value="black">Black</option>
        <option value="red">Red</option>
        <option value="blue">Blue</option>
        <option value="orange">Orange</option>
        <option value="green">Green</option>
    </select>
    <button>Add Person</button>
</form>

<style>
</style>
