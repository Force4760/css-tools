<script>
    export let value;
    export let text;
</script>

<style>
    .colorcontainer {
        width: 100%;
        max-width: 700px;
        text-align: left;
        margin: auto;
    }

    p {
        color: white;
        margin-bottom: 0px;
    }

    .color {
        -webkit-appearance: none;
        appearance: none;
        width: 100%;
        height: 30px;
        background: #272640;
        border: none;
        outline: none;
    }
</style>

<main>
    <div class="colorcontainer">
        <p>{text}</p>
        <input bind:value type="color" class="color" id="myColor" />
    </div>
</main>
