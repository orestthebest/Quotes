<script>
	import Quote from '#lib/components/Quote.svelte';
</script>

<svelte:head>
	<title>Inspirational Quotes</title>
</svelte:head>

<header class="mb-12 sm:mb-16 md:grid md:grid-cols-[1fr_auto] md:items-end md:gap-10">
	<div>
		<p class="text-xs font-medium tracking-[0.2em] text-muted uppercase">A small collection</p>
		<h1 class="mt-3 font-serif text-5xl leading-none sm:text-7xl">
			Inspirational <em class="text-accent">Quotes</em>
		</h1>
	</div>
	<p class="mt-5 max-w-xs text-muted md:mt-0 md:text-right">
		Five lines worth keeping. Copy one, or send it to someone.
	</p>
</header>

<section class="quotes">

	<Quote author="Socrates">
		The unexamined life is not worth living.
	</Quote>

	<Quote author="Seneca">
		While we are postponing, life speeds by.
	</Quote>

	<Quote author="Nelson Mandela">
		Education is the most powerful weapon which you can use to change the world.
	</Quote>

	<Quote author="Franklin D. Roosevelt">
		The only thing we have to fear is fear itself.
	</Quote>

	<Quote author="Vincent van Gogh">
		Great things are done by a series of small things brought together.
	</Quote>

</section>