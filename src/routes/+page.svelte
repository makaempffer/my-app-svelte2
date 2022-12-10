<script>
	import { createClient } from "@supabase/supabase-js";
const supabase = createClient('https://bwcpjydtjuosysairdux.supabase.co', 
	'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImJ3Y3BqeWR0anVvc3lzYWlyZHV4Iiwicm9sZSI6ImFub24iLCJpYXQiOjE2NzA2ODYyMDksImV4cCI6MTk4NjI2MjIwOX0.fuDpx9CM5pGZwB2HyWlQdZUOn-JKOj_12wEHs7uFsBs')
	let userEmail = "";
	let userPassword = "";
	let helperText = "";
	let errorMessage = null;
	async function signInWithEmail() {
		const {data, error} = await supabase.auth.signInWithPassword({
			email: userEmail,
			password: userPassword,
		}).then(helperText = "User Loged in correctly!.");
		const { data: { user } } = await supabase.auth.getUser();
		console.log(user);

	}

	async function signUpWithEmail() {
		const {data, error} = await supabase.auth.signUp({
			email: userEmail,
			password: userPassword,
		}).then(() => {
			helperText = "User registered successfully!.";
			signInWithEmail()
		}).catch(error => {
			console.log(error);
		})
	}

	async function signOut() {
		const {error} = await supabase.auth.signOut();
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>
<div class="justify-center flex h-full p-5">
	<div class="flex w-1/4 rounded p-5 bg-cyan-400 flex-none flex-col items-center">
	<h1 class="p-3  text-white text-2xl ">Login or Create an account to use the App</h1>
	<label class="text-white pb-3" for="email">Email: </label>
	<input
    id="email"
    class="bg-gray-100 border py-1 px-3"
    type="email"
    name="email"
	placeholder="email@example.com"
    bind:value={userEmail}
    required/>
	
	<label class="text-white pb-3" for="password">Password: </label>
	<input
    id="password"
    class="bg-gray-100 border py-1 px-3"
    type="password"
    name="password"
	placeholder="***********"
    bind:value={userPassword}
    required/>
	<div class="flex space-x-4 m-2">
		<button
			type="submit"
			on:click={() => signUpWithEmail()}
			class="rounded p-2 uppercase bg-cyan-200 hover:bg-cyan-400 duration-500 text-white">
			Sign Up
		</button>
		<button
			type="submit"
			on:click={() => signInWithEmail()}
			class="rounded p-2 uppercase bg-cyan-200 hover:bg-cyan-400 duration-500 text-white">
			Log In
		</button>
	</div>
	{#if !!helperText}
    <div
      class="border px-1 py-2 my-2 text-center text-sm {errorMessage
        ? 'bg-red-100 border-red-300 text-red-400'
        : 'bg-green-100 border-green-300 text-green-500'}">
      {helperText}
    </div>
  	{/if}
	</div>
</div>


