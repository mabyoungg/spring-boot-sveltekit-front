<script lang="ts">
	import "../app.css";
	const {children}: any = $props();
</script>

<div class="app">
	{@render children()}
</div>