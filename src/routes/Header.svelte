<script>
	import { page } from '$app/stores';

</script>

<header>
	<nav class="flex justify-center ">
		<ul class="flex space-x-10 bg-emerald-500 rounded p-3 text-white tracking-wider">
			<li class="hover:bg-emerald-300 rounded duration-500" aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
				<a href="/">Home</a>
			</li>
			<li class="hover:bg-emerald-300 rounded duration-500" aria-current={$page.url.pathname === '/projects' ? 'page' : undefined}>
				<a href="/projects">Projects</a>
			</li>
			<li class="hover:bg-emerald-300 rounded duration-500" aria-current={$page.url.pathname.startsWith('/teams') ? 'page' : undefined}>
				<a href="/teams">Teams</a>
			</li>
		</ul>
	</nav>
</header>
