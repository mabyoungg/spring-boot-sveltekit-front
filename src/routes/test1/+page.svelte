<script>
	const username = 'mabyoungg';

	let repositories = $state([]);

	$effect(async () => {
		const response = await fetch(`https://api.github.com/users/${username}/repos?per_page=10`);
		repositories = await response.json();
	});
</script>

<svelte:head>
	<title>test</title>
	<meta name="description" content="test 화면" />
</svelte:head>

<h1>{username}'s repositories</h1>
<ul>
	{#each repositories as repo}
		<li>
			{repo.name}
		</li>
	{/each}
</ul>