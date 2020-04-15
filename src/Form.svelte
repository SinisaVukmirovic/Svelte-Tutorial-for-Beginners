<script>
    // displatch custom event
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    // we need to create custom event dispatch handler to forward this event to the parent component that is calling this event

    let formName;
    let formBeltColor;
    let formAge;

    // let fighting = false;
    // let spells = false;
    // let agility = false;

    // group values binding (same as the above but not as messy)
    let skills = [];

    const handleSubmit = () => {
        console.log(formName, formBeltColor, formAge);
        // console.log(fighting, spells, agility);
        console.log(skills);

        const person = {
            name: formName,
            belt: formBeltColor,
            age: formAge,
            // skills: skills,
            skills,
            id: Math.random()
        };

        dispatch('addPerson', person);
    };

</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="Name..." bind:value={formName}>
    <!-- <input type="text" placeholder="Belt color..." bind:value={formBeltColor}> -->
    <input type="number" placeholder="Age" bind:value={formAge}>

    <!-- <label>Skills:</label>
    <input type="checkbox" bind:checked={fighting}> Fighting <br>
    <input type="checkbox" bind:checked={spells}> Spells <br>
    <input type="checkbox" bind:checked={agility}> Agility <br> -->

    <!-- group values binding -->
    <label>Skills:</label>
    <input type="checkbox" bind:group={skills} value="Fighting"> Fighting <br>
    <input type="checkbox" bind:group={skills} value="Spells"> Spells <br>
    <input type="checkbox" bind:group={skills} value="Agility"> Agility <br>

    <select bind:value={formBeltColor}>
        <option value="black">Black</option>
        <option value="red">Red</option>
        <option value="blue">Blue</option>
        <option value="orange">Orange</option>
    </select>

    <button>Add Ninja</button>
</form>

<style>

</style>