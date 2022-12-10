<script>
	import Header from './Header.svelte';
	import "../app.css";
</script>

<div class="bg-black w-screen h-screen">
	<Header />

	<main>
		<slot />
	</main>


</div>
