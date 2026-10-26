<script>
    let {children, author} = $props();
    let quoteElement;

     async  function copy() {
    
     await  navigator.clipboard.writeText(quoteElement.innerText.trim());


     let permission = Notification.permission;
     if (permission === "granted") {
        new Notification("Quote copied to clipboard!");
     } else if (permission !== "denied") {
        let permission = await Notification.requestPermission();
        if (permission === "granted") {
            new Notification("Quote copied to clipboard!"), {
                body: "You successfully copied the Quote"
            };
        }
    }
}


async function share(){

    await navigator.share({
        title: "Please read my quote",
        text: quoteElement.innerText.trim()
    });
}


</script>

<div class="border-t border-ink/15 py-10 sm:py-12">
    <header class="mb-4 text-xs font-medium tracking-[0.2em] text-muted uppercase">
        {author} says:
    </header>

    <blockquote
        bind:this={quoteElement}
        class="font-serif text-2xl leading-snug text-balance sm:text-[2rem]"
    >
        {@render children?.()}
    </blockquote>

    <div class="mt-6 flex gap-2">
        <button
            class="rounded-full border border-ink/20 px-4 py-2 text-sm transition-colors hover:border-ink hover:bg-ink hover:text-paper"
            type="button"
            onclick={copy}
        >
            Copy
        </button>
        <button
            class="rounded-full border border-ink/20 px-4 py-2 text-sm transition-colors hover:border-ink hover:bg-ink hover:text-paper"
            type="button"
            onclick={share}
        >
            Share
        </button>
    </div>
</div>