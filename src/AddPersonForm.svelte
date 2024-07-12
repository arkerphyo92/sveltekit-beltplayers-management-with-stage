<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    let name;
    let age;
    let skills = [];
    let beltColor;

    const subumitData = (e) => {
        const person = {
            name : name,
            age : age,
            beltColor : beltColor,
            skills : skills,
            id : Math.random()
        }
        dispatch('addPerson', person);
        dispatch('showModal', false);
    }
</script>

<div>
    <h3>Add a new person</h3>
    <form on:submit|preventDefault = {subumitData}>
        <input type="text" placeholder="name" bind:value={name}>
        <input type="number" placeholder="age" bind:value={age}>
        <label for="skills">skills</label>
        blowing<input type="checkbox" bind:group={skills} value="blowing"><br>
        sucking<input type="checkbox" bind:group={skills} value="sucking"><br>
        swallowing<input type="checkbox" bind:group={skills} value="swallowing"><br>       


    <select bind:value={beltColor}>Selected Belt
        <option value="Black">Black</option>
        <option value="Gold">Gold</option>
        <option value="Green">Green</option>
        <option value="Yellow">Yellow</option>        
    </select>

    <button type="submit">Submit</button> 
    </form>
</div>

<style>

</style>