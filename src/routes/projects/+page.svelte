<svelte:head>
	<title>Projects</title>
	<meta name="description" content="Projects" />
</svelte:head>


<script>
	import { onMount } from "svelte";
	onMount(() => {
		console.log("Mounted!.") 
	})

</script>

<div class="flex p-5">
	<div class="flex flex-col w-1/3 md:w-1/6 rounded content-evenly space-y-3 p-3 bg-cyan-500">
		<button class="bg-cyan-300 rounded p-3 text-white hover:bg-cyan-400 duration-500">New Project</button>
		<button class="bg-cyan-300 rounded p-3 text-white hover:bg-cyan-400 duration-500">Open Project</button>
	</div>
</div>
