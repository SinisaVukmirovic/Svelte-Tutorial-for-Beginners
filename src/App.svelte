<script>
	let name = 'Yoshi';
	let beltClr = 'black';

	const handleClick = () => {
		beltClr = 'red';
	};

	const handleInput = (e) => {
		beltClr = e.target.value;
	};
</script>

<main>
	<h1>Hello {name}!</h1>
	<p style="color:{beltClr}">{beltClr} belt!</p>

	<button on:click={handleClick}>Update belt color</button>

	<!-- two way data binding -->
	<!-- <input type="text" on:input={handleInput} value={beltClr}> -->

	<!-- shorthand way of doing the above -->
	<input type="text" bind:value={beltClr}>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>