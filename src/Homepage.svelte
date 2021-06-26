<script>
    import { Link } from "svelte-navigator"
</script>

<style>
	.Link-container {
		padding: 5%;
		font-family: Roboto, Arial, Helvetica, sans-serif;
        color: white;
	}

	.Link-container > header {
		font-size: 64px;
	}

	.Link {
		transition-duration: 0.2s;
	}

    .Link > :global(a) {
        color: inherit;
        font-size: 32px;
    }

	.Link:hover {
		padding-left: 6px;
	}

    .LinkList {
        list-style: none;
    }
</style>

<div class="Link-container">
	<header>Cooky Game Studio</header>

    <ul class="LinkList">

        <li>
            <div class="Link">
                <Link to="games">Games</Link>
            </div>
        </li>

        <li>
            <div class="Link">
                <Link to="about">About</Link>
            </div>
        </li>

    </ul>
</div>