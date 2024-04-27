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
	<form class="flex gap-2" on:submit|preventDefault={fetchRepositories}>
		<input class="input input-bordered" type="text" bind:value={username} placeholder="GitHub 사용자 이름 입력"/>
		<button class="btn btn-primary" type="submit">가져오기</button>
	</form>

	{#if username}
		<h1 class="font-bold">{username}'s repositories</h1>
		<ul class="mt-2 grid gap-2">
			{#each repositories as repo}
				<li>
					<div class="card bg-base-100 shadow-xl">
						<div class="card-body">
							<h2 class="card-title">{repo.name}</h2>
						</div>
					</div>
				</li>
			{/each}
		</ul>
	{/if}
</div>