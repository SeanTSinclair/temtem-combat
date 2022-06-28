<script context="module">
    export function load({ error }) {
        return {
            props: { errorMessage: error.message }
        };
    }
</script>

<script>
    export let errorMessage;
</script>

<div class="error">
    <img src="https://static.wikia.nocookie.net/temtem_gamepedia_en/images/7/7b/Smolzy_sticker.png" />
    <img src="https://img.icons8.com/color/48/000000/error.png" />
    <h1>404 Not Found</h1>
    <p>{errorMessage}</p>
</div>

<style>
    .error {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 2rem;
        text-align: center;
        margin: 0 auto;
        max-width: 1200px;
    }
    .error img:nth-child(2) {
        width: 100px;
        margin-top: 50px;
    }
</style>