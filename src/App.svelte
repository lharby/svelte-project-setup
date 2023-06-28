
<script>
	let inputPassword = "";
	let passwords = [];
  let errorMessage = "";
  let formState = "";

	function savePassword() {
    if (inputPassword.length <= 5 ) {
      errorMessage = 'Too short';
      formState = 'invalid';
      return;
    } else if (inputPassword.length >= 10) {
      errorMessage = 'Too long';
      formState = 'invalid';
      return;
    }
		passwords = [...passwords, {
			id: Math.random(),
			inputPassword: inputPassword
		}];
    errorMessage = "";
    formState = 'valid';
	}

  function removePassword(index) {
    passwords = passwords.filter((pw, idx) => {
      return idx !== index;
    });
  }

</script>

<style>

</style>

<div class="form-control">
  <input type="text" bind:value={inputPassword}>
</div>

<div class="form-control">
  <button on:click={savePassword}>Save password</button>
</div>

<div class="form-control">
  <ul>
    {#each passwords as item, index (item.id)}
      <li>{item.inputPassword} / {item.id.toString()} &nbsp; &nbsp; &nbsp; <a href="#id" on:click|preventDefault={removePassword.bind(this, index)}>x</a></li>
    {/each}
  </ul>
</div>

<div class="form-control">
  {#if formState === 'valid'}
  Password: {inputPassword}
{:else if formState === 'invalid'}
  <p>Error: {errorMessage}</p>
{/if}
</div>

<!-- <h1>Assignment</h1>
<p>Solve these tasks.</p>
<ol>
	<li>Add a password input field and save the user input in a variable.</li>
	<li>Output "Too short" if the password is shorter than 5 characters and "Too long" if it's longer than 10.</li>
	<li>Output the password in a paragraph tag if it's between these boundaries.</li>
	<li>Add a button and let the user add the passwords to an array.</li>
	<li>Output the array values (= passwords) in a unordered list (ul tag).</li>
	<li>Bonus: If a password is clicked, remove it from the list.</li>
</ol> -->