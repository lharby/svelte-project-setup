<script>
	let name = 'Luke';
	let age = 20;

	function incrementAge() {
		age += 1;
	}
</script>

<style>
	h1 {
		color: #555;
	}
</style>

<h1>Hello {name}! My age is {age}!</h1>
<button on:click="{incrementAge}">Change age</button>
