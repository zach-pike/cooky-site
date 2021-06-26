<script>
    export let gameName;
    export let description;
    export let imageURL;

    import { Link } from "svelte-navigator";
    import { breakpoint } from "./mediaquery.svelte"
</script>

<div class="GameCard">
    <img src={imageURL} width="100%" alt="Logo" />

    <div class="GameCardBody">
        {#if $breakpoint >= 3}
            <header class="DesktopHeader">{gameName}</header>

            <p class="DesktopBody">{description}</p>
            {:else}
            <header class="MobileHeader">{gameName}</header>

            <p class="MobileBody">{description}</p>
        {/if}
    </div>

    <footer>
        <Link to={`/games/${gameName}`}>See More about {gameName}</Link>
    </footer>
</div>

<style>
    .GameCard {
        width: min-content;
        height: 30%;
        padding: 0;
        background-color: #eee;
        transition-duration: 0.3s;
    }

    .GameCard > .GameCardBody {
        word-wrap: break-word;
        padding: 5px;

        height: 100%;
    }

    .GameCard > footer {
        margin-top: auto;
        padding: 8px;
    }

    .GameCard:hover {
        box-shadow: 0px 0px 8px #000;
    }


    .MobileHeader {
        font-size: 8vw;
    }

    .DesktopHeader {
        font-size: 2vw;
    }

    .MobileBody {
        font-size: 4vw;
    }

    .DesktopBody {
        font-size: 1vw;
    }
</style>
