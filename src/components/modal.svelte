<script>
    import Btn from "./btn.svelte";

    export let show = false;
    export let text;
    const close = () => {
        show = !show;
    };
    function copyToClipboard() {
        var elem = document.createElement("textarea");
        var cssT = document.getElementById("css-text");
        document.body.appendChild(elem);
        elem.value = cssT.textContent;
        elem.select();
        document.execCommand("copy");
        document.body.removeChild(elem);
        close();
    }
</script>

<style>
    .background {
        margin: none;
        padding: 0;
        border: none;
        z-index: 10;
        position: absolute;

        width: 100vw;
        height: 100vh;
    }
    .container {
        margin: none;
        padding: 0;
        border: none;
        display: flex;
        align-items: center;
        justify-content: center;
        position: absolute;
        width: 100vw;
        height: 100%;
        z-index: 20;
        overflow: hidden;
    }
    .modal {
        position: absolute;
        background-color: #242424;
        width: 500px;
        max-width: 70vw;
        height: 70vh;
        margin: auto auto;
        z-index: 20;
        border-radius: 20px;
        display: flex;
        flex-direction: column;
        overflow: hidden;
        align-items: center;
        justify-content: space-around;
        color: white;
        padding-left: 32px;
        padding-right: 32px;
    }
</style>

{#if show}
    <div class="container">
        <div class="background" on:click={close} />
        <div class="modal">
            <p id="css-text">{text || 'CSS goes here!'}</p>
            <Btn text="COPY!" calc={copyToClipboard} />
        </div>
    </div>
{/if}
