<script>
	import ContactCard from "./ContactCard.svelte";
	
	let name = 'Luke';
	let jobTitle = 'Front end developer';
	let jobDescription = 'Code plonker';
	let userImage = 'https://media.licdn.com/dms/image/C4E03AQGkiwtadr_YRA/profile-displayphoto-shrink_400_400/0/1547679348401?e=1692835200&v=beta&t=FmvE1BQZ4PyvauIH2SzgCmgvfMdRCvp2kVvwaM3R8kE';
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
		color: purple;
	}
</style>

<h1>Hello {uppercaseName}! My age is {age}!</h1>
<button on:click={incrementAge}>Increment age</button>
<p><input type="text" bind:value={name}></p>
<p><input type="text" bind:value={jobTitle}></p>
<p><input type="text" bind:value={jobDescription}></p>
<p><input type="text" bind:value={userImage}></p>
<ContactCard userName={name} jobTitle={jobTitle} jobDescription={jobDescription} userImage={userImage} />