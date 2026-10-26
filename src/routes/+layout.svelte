<script>
	import './layout.css';
	import favicon from '#lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<meta name="theme-color" content="#f2efe6" />
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
	<link
		href="https://fonts.googleapis.com/css2?family=Besley:ital,wght@0,400;0,600;1,400;1,600&family=Familjen+Grotesk:wght@400;500&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<div class="flex min-h-dvh flex-col">
	<div class="flex h-1.5" aria-hidden="true">
		<span class="flex-1 bg-tomato"></span>
		<span class="flex-1 bg-teal"></span>
		<span class="flex-1 bg-mustard"></span>
		<span class="flex-1 bg-plum"></span>
		<span class="flex-1 bg-cobalt"></span>
	</div>

	<nav class="border-b border-ink/10">
		<div class="mx-auto flex max-w-3xl items-center justify-between px-5 py-4 sm:px-8">
			<a href="/" class="font-serif text-2xl italic">Quotes</a>
			<span class="text-xs tracking-[0.2em] text-muted uppercase">Vol. 01</span>
		</div>
	</nav>

	<main class="mx-auto w-full max-w-3xl flex-1 px-5 py-14 sm:px-8 sm:py-20">
		{@render children()}
	</main>

	<footer class="border-t border-ink/10">
		<div class="mx-auto flex max-w-3xl justify-between px-5 py-6 text-xs text-muted sm:px-8">
			<span>Orest Bashi · 5B</span>
			<span>HTL Shkodër</span>
		</div>
	</footer>
</div>