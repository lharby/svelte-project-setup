<script>
	let name = 'Luke';
	let age = 50;

	function incrementAge() {
		age += 1;
	}

	function changeName() {
		name = 'Susan';
	}

	function nameInput(event) {
		const enteredValue = event.target.value;
		name = enteredValue;
	}

	$: uppercaseName = name.toUpperCase();

	$: console.log(name);

	$: if (name === 'Susan') {
		age = 55;
	}

</script>

<style>
	h1 {
		color: #333;
	}
</style>

<h1>Hello {uppercaseName}! My age is {age}!</h1>
<button on:click={incrementAge}>Increment age</button>
<!-- <button on:click={changeName}>Change name</button> -->
<!-- <input type="text" value={name} on:input={nameInput}> -->
<input type="text" bind:value={name}>