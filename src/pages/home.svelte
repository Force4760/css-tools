<script>
    //imports

    import Nav from "../components/nav.svelte";
</script>

<style>
    .container {
        display: flex;
        align-items: center;
        justify-content: start;
        flex-direction: column;
        flex-wrap: wrap;
        margin: auto;
        width: 700px;
        max-width: 100%;
    }
    .container h1 {
        flex: 1;
        color: white;
        font-size: 3rem;
        margin-bottom: 20px;
    }
    .container div {
        display: flex;
        flex-direction: column;
        color: white;
        align-items: center;
        justify-content: center;
    }
    .btn {
        width: 700px;
        max-width: 100%;
        margin: 20px auto;
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
    }
    main {
        overflow-x: hidden;
        padding: 32px;
        height: 90vh;
        display: flex;
        flex-direction: column;
    }
    a {
        text-decoration: none;
        width: 110px;
        text-align: center;
        color: #fff;
        border-radius: 5px;
        margin: auto;
        margin-bottom: 20px;
        padding: 10px;
        border: none;
        font-family: "Lato", sans-serif;
        font-weight: 500;
        background: #4d194d;
        cursor: pointer;
        transition: all 0.5s ease;
        display: inline-block;
        outline: none;
        box-shadow: 0 3px 1px -2px rgba(0, 0, 0, 0.2),
            0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12);
    }

    a:hover {
        background: #351135;
        box-shadow: 0 2px 4px -1px rgba(0, 0, 0, 0.2),
            0 4px 5px 0 rgba(0, 0, 0, 0.14), 0 1px 10px 0 rgba(0, 0, 0, 0.12);
    }

    @media (max-width: 600px) {
        .container {
            align-items: flex-start;
        }
        .container div {
            align-items: flex-start;
        }
    }
</style>

<Nav />

<main>
    <div class="container">
        <h1>CSS TOOLS</h1>
        <div>
            <p>To help people with CSS!</p>
            <p>
                Customize Borders, Box shadow, Gradients, Image filters and many
                more!
            </p>
            <p>
                Copy the CSS code you generate so that you can use it in your
                own projects!
            </p>
        </div>
    </div>

    <div class="btn">
        <a href="#/box">Box</a>
        <a href="#/gradient">Gradient</a>
        <a href="#/filter">Filter</a>
    </div>
</main>
