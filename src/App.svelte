<script>
	import Modal from './Modal.svelte';
	import AddPersonForm from './AddPersonForm.svelte';

	let showModal = false;
	let beltColor = "Black";
	const changeBeltColor = () => {
		beltColor = "Red";
	}
	// const inputHandler = (e) => {
	// 	beltColor = e.target.value;
	// }
	let firstName = "Arkar";
	let lastName = "Phyo";
	$: fullName = `${firstName} ${lastName}`;

	let people = [
		{ name:'Arkar', beltColor:'Black', age:32, id:1 },
		{ name:'Nan', beltColor:'Red', age:34, id:2 },
		{ name:'Zay', beltColor:'Yellow', age:19, id:3 }
	];

	const removeHandler = (id) => {
		people = people.filter(person => person.id != id);
	}

	const toggleModal = () => {
		showModal = !showModal
	}

	const addingPerson = (e) => {
		let person = e.detail;
		people = [person, ...people];
	}

</script>

<Modal showModal={showModal} on:click={toggleModal}>
	<AddPersonForm on:addPerson={addingPerson} on:addPerson={toggleModal}/>
</Modal>
<main>
	<button on:click="{toggleModal}">Click</button>
	<p style="color:{beltColor}">{fullName} {beltColor} Belt</p>
	<button on:click={changeBeltColor}>Belt</button>
	<input type="text" bind:value="{firstName}">
	<input type="text" bind:value="{lastName}">
	<!-- <input type="text" on:input={inputHandler} value="{beltColor}"> -->
	<input type="text" bind:value="{beltColor}">

	
	{#each people as person (person.id) }
		{#if person.beltColor == 'Black'}
			<h4>Master</h4>
			<button on:click={()=>{removeHandler(person.id)}}>Delete</button>
			<p>Name : {person.name} {person.age} years old.</p>
			<p>Belt : {person.beltColor}</p>
		{:else}
			<h4>Junior</h4>
			<button on:click={()=>{removeHandler(person.id)}}>Delete</button>
			<p>Name : {person.name} {person.age} years old.</p>
			<p>Belt : {person.beltColor}</p>
		{/if}
	{:else} <p>There are no people to show.</p>
	{/each}
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