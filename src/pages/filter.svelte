<script>
    //imports
    import { bind } from "svelte/internal";
    import Btn from "../components/btn.svelte";
    import Color from "../components/color.svelte";
    import Input from "../components/input.svelte";
    import Modal from "../components/modal.svelte";
    import Nav from "../components/nav.svelte";
    import Select from "../components/select.svelte";
    import Slider from "../components/slider.svelte";
    import Slider2 from "../components/slider2.svelte";

    let show = false;

    let property = "Blur";
    const propList = [
        "Blur",
        "Brightness",
        "Contrast",
        "Gray Scale",
        "Hue Rotate",
        "Invert",
        "Saturate",
        "Sepia",
    ];

    let blur = 0;
    let brightness = 1;
    let contrast = 1;
    let grayscale = 0;
    let hue = 0;
    let invert = 0;
    let saturate = 1;
    let sepia = 0;
    const filter = (
        prop,
        blur,
        brightness,
        contrast,
        grayscale,
        hue,
        invert,
        saturate,
        sepia
    ) => {
        if (prop === "Blur") {
            return `blur(${blur}px)`;
        } else if (prop === "Brightness") {
            return `brightness(${brightness})`;
        } else if (prop === "Contrast") {
            return `contrast(${contrast})`;
        } else if (prop === "Gray Scale") {
            return `grayscale(${grayscale})`;
        } else if (prop === "Hue Rotate") {
            return `hue-rotate(${hue}deg)`;
        } else if (prop === "Invert") {
            return `invert(${invert})`;
        } else if (prop === "Saturate") {
            return `saturate(${saturate})`;
        } else if (prop === "Sepia") {
            return `sepia(${sepia})`;
        }
    };

    $: realFil = filter(
        property,
        blur,
        brightness,
        contrast,
        grayscale,
        hue,
        invert,
        saturate,
        sepia
    );
    const modalOC = () => {
        show = !show;
    };

    $: styles = {
        filter: `${realFil}`,
    };

    $: cssVarStyles = Object.entries(styles)
        .map(([key, value]) => `--${key}:${value}`)
        .join(";");
    $: css = `
        filter: ${realFil};
    `;
</script>

<style>
    .btn {
        width: 700px;
        max-width: 100%;
        margin: 20px auto;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    main {
        overflow-x: hidden;
        padding: 32px;
    }
    .container {
        display: flex;
        height: 300px;
        width: 100%;
        align-items: center;
        justify-content: center;
    }
    .box {
        width: 500px;
        max-width: 90vw;
        height: 200px;
        background: url("https://images.unsplash.com/photo-1501785888041-af3ef285b470?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80")
            center center;
        filter: var(--filter);
    }
</style>

<Nav />
<Modal text={css} bind:show />
<main style={cssVarStyles}>
    <div class="container">
        <div class="box" />
    </div>
    <Select ops={propList} name="Filter" bind:value={property} />
    {#if property === 'Blur'}
        <Slider2 min="0" max="100" text="Blur" bind:value={blur} />
    {:else if property === 'Brightness'}
        <Slider2
            min="0"
            max="10"
            step="0.1"
            text="Brightness"
            bind:value={brightness} />
    {:else if property === 'Brightness'}
        <Slider2
            min="0"
            max="10"
            step="0.1"
            text="Brightness"
            bind:value={brightness} />
    {:else if property === 'Contrast'}
        <Slider2
            min="0"
            max="10"
            step="0.1"
            text="Contrast"
            bind:value={contrast} />
    {:else if property === 'Gray Scale'}
        <Slider2
            min="0"
            max="1"
            step="0.01"
            text="Gray Scale"
            bind:value={grayscale} />
    {:else if property === 'Hue Rotate'}
        <Slider2 min="0" max="360" text="Hue Rotate" bind:value={hue} />
    {:else if property === 'Invert'}
        <Slider2
            min="0"
            max="1"
            step="0.01"
            text="Invert"
            bind:value={invert} />
    {:else if property === 'Saturate'}
        <Slider2
            min="0"
            max="10"
            step="0.1"
            text="Saturate"
            bind:value={saturate} />
    {:else if property === 'Sepia'}
        <Slider2 min="0" max="1" step="0.01" text="Sepia" bind:value={sepia} />
    {/if}
    <div class="btn">
        <Btn text="CSS!" calc={modalOC} />
    </div>
</main>
