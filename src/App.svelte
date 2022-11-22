<script>
	let name = 'Jinny'
	let age = 29

	function incrementAge() {
		age++;
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello  My name is {name}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>