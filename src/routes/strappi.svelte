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
	<a href="tel:{directory.phone_number}">{directory.phone_number}</a>
    <hr>
    {/each}
{:catch error}
	<p>An error occurred!</p>
{/await}