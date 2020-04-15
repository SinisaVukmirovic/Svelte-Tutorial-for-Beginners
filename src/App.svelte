<script>
	// components
	import Modal from './Modal.svelte';

	// forms
	import Form from './Form.svelte';

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

	// event forwarding
	let showModal = false;

	const toggleModal = () => {
		showModal = !showModal;
	};

	// slots
	let showSlotModal = false;

	const toggleSlotModal= () => {
		showSlotModal = !showSlotModal;
	};

	// forms
	let showForm = false;

	const openForm= () => {
		showForm = !showForm;
	};

	// custom event dispatch
	const addPerson = (e) => {
		console.log(e.detail);

		const person = e.detail;

		people = [person, ...people];

		showForm = false;
	};
</script>

<!-- components -->
<!-- and props -->
<!-- <Modal propsMsg="Hey, I am a prop value!" isPromotion={true} showModal={showModal}/> -->
																	   <!-- event forwarding -->
<Modal propsMsg="Hey, I am a prop value!" isPromotion={true} {showModal} on:click={toggleModal}/>
														<!-- when prop name and 
															value variable name
															are the same, we can use 
															shorthand {showModal}-->

<!-- slots -->
<Modal propsMsg="" {showSlotModal} on:click={toggleSlotModal}>
	<h3>Add a new person</h3>

	<!-- named slots -->
	<div slot="details">
		<h5>Add a new Ninja and his belt color!</h5>
	</div>
</Modal>

<!-- forms -->
<Modal propsMsg="" {showForm} on:click={openForm}>
	<!-- utilizing custom event dispatch here on form -->
	<Form on:addPerson={addPerson} />
</Modal>

<main>
	<h2>reactive values | binding values/two way data binding</h2>
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
	<h2>loops | conditionals | event handlers</h2>
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
		 which means that svelte can use that key to keep track of which DOM
		 element is connected to which item in the array
		 useful for manipulating data, later on -->

	<hr>
	<h2>conditionals</h2>
	<!-- conditionals -->
	{#if num > 20}
		<p>Num is greater than 20!</p>
	{:else if num > 5}
		<p>Num is greater than 5!</p>
	{:else}
		<p>Num is not greater than 5!</p>
	{/if}

	<hr>
	<h2>events | props | conditional styles | event forwarding and event modifiers</h2>

	<button on:click={toggleModal}>Show Modal</button>
	<!-- open modal button that works only once with event modifier -->
	<button on:click|once={toggleModal}>Show Modal Once</button>

	<hr>
	<h2>slots/named slots & forms</h2>

	<button on:click={toggleSlotModal}>Show Slot Modal</button>

	<button on:click={openForm}>Open Form</button>

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

	h2 {
		color: cornflowerblue;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>