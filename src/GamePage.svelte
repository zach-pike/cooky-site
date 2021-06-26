<script>
    export let gameTitle;

    import games from "./games.json"

    let gameInfo = games[gameTitle]

    import SvelteMarkdown from 'svelte-markdown'
</script>

<style>
    .GameTitle {
        color: #eee;
    }

    .GameContainer {
        padding: 5%;
    }

    .markdown {
        color: black;
        font-family: Roboto, Arial, Helvetica, sans-serif;
        overflow-y: auto;
        max-height: 73vh;
    }
</style>

<div class="GameContainer">
    <h1 class="GameTitle">{gameTitle}</h1>

    <div class="markdown">
        {#await fetch(`/GamePages/${gameTitle}.md`)}
            <p>Loading Page</p>
        {:then data}

            {#await data.text()}
                <p>Loading...</p>
            {:then text} 
                <SvelteMarkdown source={text} />
            {/await}

        {:catch error}
            <h3>Failed to load page for {gameTitle}</h3>
        {/await}
    </div>
</div>