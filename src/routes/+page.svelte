<script>
	import Quote from '#lib/components/Quote.svelte';

	let quotes = $state([
		{
			id: 'socrates',
			author: 'Socrates',
			text: 'The unexamined life is not worth living.',
			column: 'left'
		},
		{
			id: 'seneca',
			author: 'Seneca',
			text: 'While we are postponing, life speeds by.',
			column: 'left'
		},
		{
			id: 'mandela',
			author: 'Nelson Mandela',
			text: 'Education is the most powerful weapon which you can use to change the world.',
			column: 'left'
		},
		{
			id: 'roosevelt',
			author: 'Franklin D. Roosevelt',
			text: 'The only thing we have to fear is fear itself.',
			column: 'left'
		},
		{
			id: 'vangogh',
			author: 'Vincent van Gogh',
			text: 'Great things are done by a series of small things brought together.',
			column: 'left'
		}
	]);

	function startDrag(event, id) {
		event.dataTransfer.setData('text/plain', id);
		event.dataTransfer.effectAllowed = 'move';
	}

	function allowDrop(event) {
		event.preventDefault();
		event.dataTransfer.dropEffect = 'move';
	}

	function dropQuote(event, column) {
		event.preventDefault();
		const id = event.dataTransfer.getData('text/plain');
		const quote = quotes.find((item) => item.id === id);

		if (quote) quote.column = column;
	}
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

<section class="grid gap-6 md:grid-cols-2">
	<div
		aria-label="Red quote area"
		class="min-h-64 rounded-2xl bg-red-100 p-5 sm:p-6"
		ondragover={allowDrop}
		ondrop={(event) => dropQuote(event, 'left')}
		role="list"
	>
		<h2 class="mb-2 text-sm font-medium uppercase tracking-wider">Quotes</h2>
		{#each quotes.filter((quote) => quote.column === 'left') as quote (quote.id)}
			<div
				class="cursor-grab active:cursor-grabbing"
				draggable="true"
				ondragstart={(event) => startDrag(event, quote.id)}
				role="listitem"
			>
				<Quote author={quote.author}>{quote.text}</Quote>
			</div>
		{/each}
	</div>

	<div
		aria-label="Blue quote area"
		class="min-h-64 rounded-2xl bg-blue-100 p-5 sm:p-6"
		ondragover={allowDrop}
		ondrop={(event) => dropQuote(event, 'right')}
		role="list"
	>
		<h2 class="mb-2 text-sm font-medium uppercase tracking-wider">Favorites</h2>
		{#each quotes.filter((quote) => quote.column === 'right') as quote (quote.id)}
			<div
				class="cursor-grab active:cursor-grabbing"
				draggable="true"
				ondragstart={(event) => startDrag(event, quote.id)}
				role="listitem"
			>
				<Quote author={quote.author}>{quote.text}</Quote>
			</div>
		{/each}
	</div>
</section>