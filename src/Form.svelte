<script>
    let formName;
    let formBeltColor;
    let formAge;

    const handleSubmit = () => {
        console.log(formName, formBeltColor, formAge);
    };
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="Name..." bind:value={formName}>
    <input type="text" placeholder="Belt color..." bind:value={formBeltColor}>
    <input type="number" bind:value={formAge}>
    <button>Add Ninja</button>
</form>

<style>

</style>