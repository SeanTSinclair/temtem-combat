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

<div class="container flex flex-col m-auto items-center">
    <div class="my-4 mx-4">
        <h1 class="font-medium text-2xl">Welcome</h1>
        <p>This temtem site is a hobby project meant to aid in finding out what types are effective in a combat situation.</p>
        <p>Search for the temtem and select which slot it should go to to find optimal type combinations for your combat encounter!</p>
    </div>

        <input type="text" class="max-w-min p-2 m-auto my-2 bg-transparent border-2 border-neutral-400 rounded-md" placeholder="Search" bind:value={search} on:input={searchTemtems}/>
        {#if searchResults.length > 0}
            <div class="temtem-container grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 my-4">
                {#each searchResults as temtem}
                    <div class="temtem">
<!--                        <div class="combat-buttons">-->
<!--                            <button class="slot-one" on:click={() => slotOneLocal = temtem}>Slot 1</button>-->
<!--                            <button class="slot-two" on:click={() => slotTwoLocal = temtem}>Slot 2</button>-->
<!--                        </div>-->
                        <TemtemCard temtem={temtem} />
                    </div>
                {/each}
            </div>
        {/if}

<!--    <CombatDisplay />-->

</div>