<script>
    export let open = false;
</script>

<style>
    aside {
        left: -110%;
        transition: left 0.5s ease-in-out;
        z-index: 50;
        width: 700px;
        max-width: 80%;
        height: 100%;
        position: absolute;
        background: #10353f;
        box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.3);
    }

    .open {
        left: 0;
    }
    nav {
        padding-left: 22px;
        padding-top: 50px;
        font-size: larger;
    }
    a {
        font-size: larger;
        display: block;
        color: white;
    }
</style>

<aside class:open>
    <nav>
        <a href="#/box">Box</a>
        <a href="#/gradient">Gradient</a>
        <a href="#/filter">Filter</a>
        <a href="#/text">Text</a>
    </nav>
</aside>
