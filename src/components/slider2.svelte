<script>
    export let value;
    export let text;
    export let min;
    export let max;
    export let step = "1";
</script>

<style>
    .slidecontainer {
        width: 100%;
        max-width: 700px;
        text-align: left;
        margin: auto;
    }

    p {
        color: white;
        margin-bottom: 3px;
    }

    .slider {
        -webkit-appearance: none;
        appearance: none;
        width: 100%;
        height: 15px;
        background: #272640;
        border: none;
        outline: none;
        opacity: 0.7;
        -webkit-transition: 0.2s;
        transition: opacity 0.2s;
    }

    .slider:hover {
        opacity: 1;
    }

    .slider::-webkit-slider-thumb {
        -webkit-appearance: none;
        appearance: none;
        width: 25px;
        height: 25px;
        background: #4d194d;
        cursor: pointer;
        border-radius: 50%;
    }

    .slider::-moz-range-thumb {
        width: 25px;
        height: 25px;
        background: #4d194d;
        cursor: pointer;
    }
</style>

<main>
    <div class="slidecontainer">
        <p>{text}</p>
        <input
            bind:value
            type="range"
            {min}
            {max}
            {step}
            class="slider"
            id="myRange" />
    </div>
</main>
