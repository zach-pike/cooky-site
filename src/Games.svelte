<style>
    .Games {
        padding: 3%;
        font-family: Roboto, Arial, Helvetica, sans-serif;
    }

    .GameCardContainer {
        display: flex;
    }

    .GameCard {
        width: 15%;
        height: 30%;
        padding: 0;
        background-color: #eee;
    }

    .GameCard > .GameCardBody {
        word-wrap: break-word;
        padding: 5px;

        height: 100%;
    }

    .GameCardBody > header {
        font-size: 25px;
    }

    .GameCard > footer {
        margin-top: auto;
        padding: 8px;
    }
</style>

<script>
    import data from "./games.json"

    console.log(data)

    let games = [];

    Object.keys(data).forEach(gameName => {
        games = [...games, { "title": gameName, "description": data[gameName].desciption }]
    })

    import { Link } from "svelte-navigator"
</script>

<div class="Games">

    <h1>Games we have made</h1>

    <div class="GameCardContainer">

        {#each games as game}
            <div class="GameCard">
                <img src="/resources/placeholder.jpg" width="100%" alt="Logo" />

                <div class="GameCardBody">

                    <header>{game.title}</header>

                    <p>{game.description}</p>
                    
                </div>

                <footer>
                    <Link to="{`/games/${game.title}`}">See More about {game.title}</Link>
                </footer>

            </div>
        {/each}

    </div>
</div>