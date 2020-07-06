<script>
	const fetchDirectories = (async () => {
		const response = await fetch('https://jposso-strapi.herokuapp.com/directories')
		return response.json()
	})()
</script>

<svelte:head>
	<title>Strappi Test</title>
</svelte:head>

<h1>Directory</h1>

<hr>

{#await fetchDirectories}
	<p>...waiting</p>
{:then directories}
	{#each directories as directory}
	<b>{directory.title}</b>
	<p>{directory.phone_number}</p>
    <hr>
    {/each}
{:catch error}
	<p>An error occurred!</p>
{/await}