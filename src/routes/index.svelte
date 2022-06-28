<script context="module">
    export async function load({fetch}) {
        const response = await fetch("https://temtem-api.mael.tech/api/temtems");
        const temtems = await response.json();

        if (response.ok) {
            return { props: { temtems } }
        }
        return {
            status: response.status,
            error: new Error("Failed to load temtems")
        }
    }
</script>

<script>
    import TemtemCard from "../lib/TemtemCard.svelte";

    export let temtems;
    let search;
    let searchResults = [];

    function searchTemtems() {
        search.length > 1 ? searchResults = temtems.filter(temtem => temtem.name.toLowerCase().includes(search.toLowerCase())) : searchResults = [];
    }

</script>

<div class="main-container">
    <div class="welcome">
        <h1>Welcome</h1>
        <p>This temtem site is a hobby project meant to aid in finding out what types are effective in a combat situation.</p>
        <p>Search for the temtem and select which slot it should go to to find optimal type combinations for your combat encounter!</p>
    </div>

        <input type="text" placeholder="Search" bind:value={search} on:input={searchTemtems}/>
        {#if searchResults.length > 0}
            <div class="temtem-container">
                {#each searchResults as temtem}
                    <div class="temtem">
                        <TemtemCard temtem={temtem} />
                    </div>
                {/each}
            </div>
        {/if}
</div>

<style>
    .main-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 100px;
    }

    .welcome {
        margin: 50px;
    }

    .temtem-container {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }

    input {
        max-width: 200px;
        height: 30px;
        background-color: var(--color-secondary);
        border: 1px solid var(--color-dark);
        border-radius: 5px;
        filter: brightness(95%);
        margin : 20px 0;
    }
</style>

