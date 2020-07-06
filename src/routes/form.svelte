<script>
	let item = {
		title: "",
		phone_number: ""
	}

	const cleanItem = ()  => {
		item = {
			title: "",
			phone_number: ""
		}
	}

	const addItem = async () => {
		const newItem = {
			title: item.title,
			phone_number: item.phone_number
		}
		
		console.log(newItem);
		
		const response = await fetch('http://localhost:1337/directories', {
			method: 'POST',
 			body: JSON.stringify(newItem),
			headers:{
				'Content-Type': 'application/json'
			}
		})
		console.log(response)
		cleanItem();
		return response.json()
	};

	const onSubmitHandler = () => {
		addItem();
	};

</script>

<style>
	button {
		margin-top: 10px;
	}
</style>

<svelte:head>
	<title>Strappi Test</title>
</svelte:head>

<h1>Directory</h1>

<hr>

<form on:submit|preventDefault={onSubmitHandler}>
	<div>
		<label>Title</label>
		<input type="text" bind:value={item.title} />
	</div>
	<div>
		<label>Phone Number</label>
		<input type="number" bind:value={item.phone_number} />
	</div>
	<button type="submit">
		Enviar
	</button>
</form>