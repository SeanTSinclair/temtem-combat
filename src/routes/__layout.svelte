<script>
    import '../styles/global.css';
    import Header from "../lib/Header.svelte";
    import Footer from "../lib/Footer.svelte";
</script>
<div class="div flex flex-col justify-between h-screen">
    <Header />

    <main class="flex flex-col container m-auto">
        <slot></slot>
    </main>

    <Footer />
</div>