<script>
    import Logo from "./logo.svelte";
    import Hamburger from "./burger.svelte";

    export let sidebar = false;
    let width;
</script>

<style>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #4d194d;
        padding: 8px;
        box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.3);
    }
    nav {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: start;
        margin-left: 10px;
    }
    div {
        display: flex;
        justify-content: space-between;
        width: 100%;
        max-width: 1000px;
        margin: auto;
    }
    section {
        display: flex;
    }
    a {
        margin-left: 10px;
        margin-right: 20px;
        font-size: larger;
        display: block;
        color: white;
    }
</style>

<svelte:window bind:innerWidth={width} />
<header>
    <nav>
        {#if width < 640}
            <Hamburger bind:open={sidebar} />
            <Logo />
        {:else}
            <div>
                <Logo />
                <section class="links">
                    <a href="#/box">Box</a>
                    <a href="#/gradient">Gradient</a>
                    <a href="#/filter">Filter</a>
                    <a href="#/text">Text</a>
                </section>
            </div>
        {/if}
    </nav>
</header>
