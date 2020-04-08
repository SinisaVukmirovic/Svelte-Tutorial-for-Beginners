<script>
	// components
	import Modal from './Modal.svelte';

	// let name = 'Yoshi';
	let beltClr = 'black';

	let firstName = 'Jimmy';
	let lastName = 'Handrix';

	// reactive value
	$: fullName = `${firstName} ${lastName}`;

	$: {
		console.log(beltClr);
		console.log(fullName);
	}

	// event handlers
	const handleClick = () => {
		beltClr = 'red';
	};

	const handleInput = (e) => {
		beltClr = e.target.value;
	};

	// loops
	let people = [
		{ name: 'yoshi', beltClr: 'black', age: 25, id: 1 },
		{ name: 'mario', beltClr: 'red', age: 45, id: 2 },
		{ name: 'luigi', beltClr: 'orange', age: 35, id: 3 }
	];

	// inline event handlers
	const handleDelete = (id) => {
		// delete the person from people array
		people = people.filter(person => person.id != id);
		// we have to reasign because svelte looks for reasignment, to check
		// if something has been updated
	};

	// conditionals
	let num = -5;
</script>

<!-- components -->
<Modal />

<main>
	<!-- <h1>Hello {name}!</h1> -->
	<!-- <p style="color:{beltClr}">{beltClr} belt!</p> -->
	<!-- <p>{firstName} {lastName} - {beltClr} belt!</p> -->
	<!-- using reactive value -->
	<p>{fullName} - {beltClr} belt!</p>

	<!-- <button on:click={handleClick}>Update belt color</button> -->

	<!-- two way data binding -->
	<!-- <input type="text" on:input={handleInput} value={beltClr}> -->

	<!-- shorthand way of doing the above -->
	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={beltClr}>

	<hr>

	<!-- loops -->
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			<!-- conditional -->
			{#if person.beltClr === 'black'}
				<p><strong>MASTER NINJA</strong></p>
			{/if}
			<p>{person.age} years old, {person.beltClr} belt!</p>
			<button on:click={() => handleDelete(person.id)}>Delete</button>
			<!-- to prevent automatically invoked function, we wrap that function
			in an inline function, which is not automatically invoked when the code runs -->
		</div>
	{:else}
	<!-- if array is empty it will default to what ever is in {:else} -->
		<p>There are no people to show!</p>
	{/each}
	<!-- when using each loop in svelte, we should also apply unique key to each
		 element in array (id,in this case)
		 which means that svelte can use that key to kep track of which DOM
		 element is connected to which item in the array
		 useful for manipulating data, later on -->

	<hr>
	<!-- conditionals -->
	{#if num > 20}
		<p>Num is greater than 20!</p>
	{:else if num > 5}
		<p>Num is greater than 5!</p>
	{:else}
		<p>Num is not greater than 5!</p>
	{/if}

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	/* h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	} */

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>