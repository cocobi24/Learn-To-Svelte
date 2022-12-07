<script>
	let name = 'Jinny'
	let age = 29

	$: uppercaseName = name.toUpperCase();

	function incrementAge() {
		age++;
	}

	function changeName() {
		name = name === "Hojin"? "Jinny" : "Hojin";
	}

</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello  My name is {uppercaseName}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>
<button on:click="{changeName}">Change Name</button>