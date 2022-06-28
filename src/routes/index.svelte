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

<div class="search-container">
    <input type="text" placeholder="Search" bind:value={search} on:input={searchTemtems}/>

    {#if searchResults.length > 0}
        <ul>
            {#each searchResults as temtem}
                <TemtemCard temtem={temtem}/>
            {/each}
        </ul>
    {/if}
</div>