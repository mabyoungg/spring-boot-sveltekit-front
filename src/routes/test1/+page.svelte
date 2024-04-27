<script>
	let username = $state('');

	let repositories = $state([]);

	async function fetchRepositories() {
		const response = await fetch(`https://api.github.com/users/${username}/repos?per_page=10`);
		repositories = await response.json();
	}
</script>

<svelte:head>
	<title>test</title>
	<meta name="description" content="test 화면" />
</svelte:head>

<div class="p-5">
	<form on:submit|preventDefault={fetchRepositories}>
		<input type="text" bind:value={username} placeholder="GitHub 사용자 이름 입력"/>
		<button type="submit">데이터 가져오기</button>
	</form>

	{#if username}
		<h1>{username}'s repositories</h1>
		<ul>
			{#each repositories as repo}
				<li>
					- {repo.name}
				</li>
			{/each}
		</ul>
	{/if}
</div>