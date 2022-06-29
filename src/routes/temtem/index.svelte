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


<div class="container flex flex-col justify-center m-auto my-4">
    <h1 class="text-4xl my-4">Temtems</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
        {#each temtems as temtem}
            <div class="temtem">
                <TemtemCard temtem={temtem} />
            </div>
        {/each}
    </div>
</div>

<!--<style>-->
<!--    .temtem-container {-->
<!--        display: flex;-->
<!--        flex-wrap: wrap;-->
<!--        justify-content: center;-->
<!--    }-->
<!--</style>-->