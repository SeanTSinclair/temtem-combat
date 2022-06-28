<script context="module">
    export async function load({fetch, params}) {
        const id = params.id;
        const response = await fetch("https://temtem-api.mael.tech/api/temtems/" + id);
        const temtem = await response.json();

        if (response.ok) {
            return { props: { temtem } }
        }
        return {
            status: 301,
            // error: new Error("Failed to load temtem with id " + id)
            redirect: "/temtems"
        }
    }
</script>

<script>
    export let temtem;
</script>

<div class="temtem">
    <aside>
        <img src="https://temtem-api.mael.tech{temtem.icon}" alt="{temtem.name}">
        <table>
            <thead>
            <tr>HP</tr>
            <tr>ATK</tr>
            </thead>
            <tbody>
            <tr>{temtem.stats.hp}</tr>
            <tr>{temtem.stats.atk}</tr>
            </tbody>
        </table>
    </aside>
    <div class="content">
        <h1> <span>#{temtem.number}</span> {temtem.name}</h1>
        <div class="types">
            <h3>Types</h3>
            {#each temtem.types as type}
                <p class="type {type.toString().toLowerCase()}">{type}</p>
            {/each}
        </div>
    </div>
</div>

<style>
    .temtem {
        display: flex;
        justify-content: space-between;
        border: 2px solid var(--color-tertiary);
        padding-bottom: 100px;
    }
    aside {
        max-width: 400px;
        margin: 10px
    }
    aside img {
        max-width: 250px;
    }
    .content {
        display: flex;
        flex-direction: column;
        height: 100%;
    }

    .nature {color: green;} .wind {color: blue;} .fire {color: red;} .water {color: purple;}
    .neutral {color: gray;} .electric {color: yellow;} .mental {color:mediumpurple;} .crystal {color: lightblue;}
    .toxic {color: rebeccapurple;} .melee {color: orange;} .earth {color: brown;} .digital {color: antiquewhite;}

</style>