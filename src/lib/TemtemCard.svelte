<script>
    export let temtem;
</script>

<div class="temtem-card">
    <div class="temtem-card-row">
        <div class="row-content">
            <span>#{temtem.number}</span>
            <h2>{temtem.name}</h2>
        </div>
    </div>
    <a sveltekit:prefetch href="/temtem/{temtem.number}">
        <img src="{temtem.wikiPortraitUrlLarge}"/>
    </a>
</div>

<style>

    .temtem-card {
        flex: 0 0 28%;
        margin: 10px;
        max-width: 260px;
        background-color: var(--color-tertiary);
        border-radius: 10px;
        box-shadow:
                0px 0.5px 2.3px -5px rgba(0, 0, 0, 0.07),
                0px 1.2px 5.4px -5px rgba(0, 0, 0, 0.052),
                0px 2.1px 9.8px -5px rgba(0, 0, 0, 0.044),
                0px 3.5px 16.2px -5px rgba(0, 0, 0, 0.038),
                0px 5.8px 26.7px -5px rgba(0, 0, 0, 0.032),
                0px 10.2px 46.7px -5px rgba(0, 0, 0, 0.026),
                0px 22px 101px -5px rgba(0, 0, 0, 0.018);
    }

    .temtem-card a img {
        width: 80%;
        margin: 0 auto;
        padding: 10px;
        transition: all 0.3s ease-in-out;
    }

    .temtem-card a img:hover {
        transform: scale(1.05);
    }
    .temtem-card-row {
        background-color: var(--color-bright);
        margin: 10px 0;
        border-radius: 0 0 5px 5px;
        box-shadow:
                0px 3.1px 0.1px -3px rgba(0, 0, 0, 0.009),
                0px 5.6px 0.7px -3px rgba(0, 0, 0, 0.014),
                0px 7.5px 1.8px -3px rgba(0, 0, 0, 0.018),
                0px 8.8px 3.9px -3px rgba(0, 0, 0, 0.022),
                0px 9.7px 7.5px -3px rgba(0, 0, 0, 0.025),
                0px 10.5px 14px -3px rgba(0, 0, 0, 0.028),
                0px 11.9px 27.5px -3px rgba(0, 0, 0, 0.03),
                0px 18px 65px -3px rgba(0, 0, 0, 0.03);
    }

    .row-content {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .row-content span {
        font-size: 1.3em;
    }

    .row-content h2 {
        font-size: 1.5em;
        margin: 5px;
        max-width: 180px;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: fade;
    }
</style>