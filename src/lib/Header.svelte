<script>
    export let title = "Temtem Combat Calculator";
</script>

<header>
    <a href="/">
        <img src="/logo.png" alt="Logo">
    </a>
    <a href="/">
        <h1>{title}</h1>
    </a>
    <nav>
        <ul>
            <li><a href="/temtem">Temtems</a></li>
        </ul>
    </nav>
</header>

<style>
    header {
        display: flex;
        justify-content: center;
        margin: 0;
        padding: 20px;
        text-align: center;
        background-color: var(--color-primary);
    }
    header img {
        position: absolute;
        left: 10px;
        width: 80px;
    }
    header h1 {
        margin-left: 20px;
        font-size: 30px;
    }
    nav ul{
        display: flex;
        justify-content: center;
        flex-direction: row;
        margin: 0;
        padding: 20px;
        text-align: center;
    }
    ul li {
        padding: 0;
        list-style: none;
        margin: 10px;
    }


    @media (max-width: 420px) {
        header img {
            display: none;
        }
    }
</style>