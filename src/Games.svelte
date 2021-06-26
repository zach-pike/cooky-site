<style>
    .Games {
        padding: 3%;
        font-family: Roboto, Arial, Helvetica, sans-serif;
    }

    .GameCardContainer {
        display: flex;
    }

    .MobileGameCardContainer {
        display: flex;
        justify-content: center;
    }
</style>

<script>
    import data from "./games.json"

    console.log(data)

    let games = [];

    Object.keys(data).forEach(gameName => {
        games = [...games, { "title": gameName, "description": data[gameName].desciption }]
    })

    import { breakpoint } from "./mediaquery.svelte"
    import { Link } from "svelte-navigator"
    import GameCard from "./GameCard.svelte"

    breakpoint.subscribe((size) => {
        console.log(size)
    })
</script>

<div class="Games">

    {#if $breakpoint < 3}
        <h1 style="text-align: center;">Games we have made</h1>
        {:else}
        <h1>Games we have made</h1>
    {/if}

    {#if $breakpoint < 3}
        <div class="MobileGameCardContainer">

            {#each games as game}
                <GameCard gameName="{game.title}"
                        description="{game.description}" 
                        imageURL="/resources/placeholder.jpg"
                />
            {/each}

        </div>
        {:else}
        <div class="GameCardContainer">

            {#each games as game}
                <GameCard gameName="{game.title}"
                        description="{game.description}" 
                        imageURL="/resources/placeholder.jpg"
                />
            {/each}

        </div>
    {/if}
</div>