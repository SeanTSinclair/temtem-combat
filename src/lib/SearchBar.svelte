<script>
    let searchText = "";
</script>

<div class="search-container">
    <input type="text" placeholder="Search..." bind:value={searchText}/>
</div>

<style>
    .search-container {
        position: absolute;
        right: 0;
        top: 49px;
        padding: 0px 20px;
    }

    .search-container input {
        background-color: transparent;
        border: none;
        text-align: right;
    }
</style>