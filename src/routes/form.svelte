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
		
		const response = await fetch('https://jposso-strapi.herokuapp.com/directories', {
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
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
</svelte:head>

<h1>Directory</h1>

<hr>

<form on:submit|preventDefault={onSubmitHandler}>
	<div class="form-group">
		<label>Title</label>
		<input class="form-control" type="text" bind:value={item.title} />
	</div>
	<div class="form-group">
		<label>Phone Number</label>
		<input class="form-control" type="number" bind:value={item.phone_number} />
	</div>
	<button class="btn btn-outline-dark" type="submit">
		Enviar
	</button>
</form>