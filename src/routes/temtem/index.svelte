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
    import TemtemCard from "../../lib/TemtemCard.svelte";
    export let temtems;
</script>


<div class="temtem-container">
    {#each temtems as temtem}
        <div class="temtem">
            <TemtemCard temtem={temtem} />
        </div>
    {/each}
</div>

<style>
    .temtem-container {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
</style>