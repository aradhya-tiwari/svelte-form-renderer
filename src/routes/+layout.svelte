<script lang="ts">
	import "../app.css";

	let { children } = $props();
</script>

<main class="bg-primary-foreground">
	{@render children()}
</main>
