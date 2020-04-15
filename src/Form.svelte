<script>
    let formName;
    let formBeltColor;
    let formAge;

    const handleSubmit = () => {
        console.log(formName, formBeltColor, formAge);
        // console.log(fighting, spells, agility);
        console.log(skills);
    };

    // let fighting = false;
    // let spells = false;
    // let agility = false;

    // group values binding (same as the above but not as messy)
    let skills = [];

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