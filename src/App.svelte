<script>
	import ContactCard from "./ContactCard.svelte";

	let name = 'Jinny'
	let age = 29

	$: uppercaseName = name.toUpperCase();

	$: age = name === "Hojin"? 19 : 29;
	function incrementAge() {
		age++;
	}

	function changeName() {
		name = name === "Hojin"? "Jinny" : "Hojin";
	}

	function nameInput(event){
		const enteredValue = event.target.value;
		name = enteredValue;
	}

</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello  My name is {uppercaseName}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>
<!-- <button on:click="{changeName}">Change Name</button> -->
<!-- <input type="text" value="{name}" on:input="{nameInput}"> -->
<input type="text" bind:value="{name}">

<ContactCard userName="{name}"/>