<script context="module">

    export async function load({fetch}) {
        const response = await fetch("https://temtem-api.mael.tech/api/weaknesses");
        const weaknesses = await response.json();
        if (response.ok) {
            return { props: { weaknesses } }
        }

        return {
            status: response.status,
            error: new Error("Failed to weaknesses")
        }
    }
</script>

<script>

    export let weaknesses;

    let slotOne;
    let slotTwo;
    let weaknessesSlotOne;
    let weaknessesSlotTwo;



</script>

<div>
    {slotOneRef}
</div>

{#if slotOneRef !== undefined || slotTwoRef !== undefined}
    <div class="combat-container">
        {#if slotOneRef !== ""}
            <div class="slot">
                <div class="slot-header">
                    <p>#{slotOneRef.number}</p>
                    <b>{slotOneRef.name}</b>
                </div>
                <ul>
                    <li>Dummy</li>
                    <!--{#each weaknessesSlotOne as weakness}-->
                    <!--    <li>{weakness}</li>-->
                    <!--{/each}-->
                </ul>
            </div>
        {/if}
        {#if slotTwoRef !== ""}
            <div class="slot">
                <div class="slot-header">
                    <p>#{slotTwoRef.number}</p>
                    <b>{slotTwoRef.name}</b>
                </div>
                <ul>
                    <!--{#each weaknessesSlotTwo as weakness}-->
                    <!--    <li>{weakness}</li>-->
                    <!--{/each}-->
                </ul>
            </div>
        {/if}
    </div>
{/if}