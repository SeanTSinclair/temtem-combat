<script>
    import '../styles/global.css';
    import Header from "../lib/Header.svelte";
    import Footer from "../lib/Footer.svelte";
</script>

<Header />

<main>
    <slot></slot>
</main>

<Footer />

<style>
    main {
        display: flex;
        flex-direction: column;
        max-width: 1200px;
        margin: 0 auto;
    }
</style>