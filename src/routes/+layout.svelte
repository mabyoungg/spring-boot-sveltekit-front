<script lang="ts">
	import '$lib/app.css';
	import rq from '$lib/rq/rq.svelte';
    import { onMount } from 'svelte';

	const {children}: any = $props();

	onMount(() => {
		rq.initAuth();
	});
</script>

<header class="flex">
	<ul class="flex gap-2">
		<li>
			<a href="/" class="btn btn-link">홈</a>
		</li>
		{#if rq.isLogout()}
			<li>
				<a href="/member/login" class="btn btn-link">로그인</a>
			</li>
		{/if}
		{#if rq.isLogin()}
			<li>
				<button on:click={() => rq.logout()} class="btn btn-link">로그아웃</button>
			</li>
			<li>
				<a href="/post/myList" class="btn btn-link">내글</a>
			</li>
		{/if}
	</ul>

	<div class="flex-1"></div>

	<div>
		<a href="/member/me" class="btn btn-link">
			{rq.member.username}
		</a>
	</div>
</header>

<hr />

<main>
	{@render children()}
</main>