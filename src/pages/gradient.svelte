<script>
    //imports
    import Btn from "../components/btn.svelte";
    import Color from "../components/color.svelte";
    import Input from "../components/input.svelte";
    import Modal from "../components/modal.svelte";
    import Nav from "../components/nav.svelte";
    import Select from "../components/select.svelte";
    import Slider from "../components/slider.svelte";
    import Slider2 from "../components/slider2.svelte";

    let show = false;
    function hexToRGB(h, o) {
        let r = 0,
            g = 0,
            b = 0;

        // 3 digits
        if (h.length == 4) {
            r = "0x" + h[1] + h[1];
            g = "0x" + h[2] + h[2];
            b = "0x" + h[3] + h[3];

            // 6 digits
        } else if (h.length == 7) {
            r = "0x" + h[1] + h[2];
            g = "0x" + h[3] + h[4];
            b = "0x" + h[5] + h[6];
        }

        return "rgba(" + +r + "," + +g + "," + +b + "," + +o + ")";
    }
    let property = "Linear";
    const propList = ["Linear", "Radial"];
    let deg = 0;

    let co1 = "#0000ff";
    let co1o = 1;
    let co1p = 0;
    let co2 = "#ff0000";
    let co2o = 1;
    let co2p = 100;
    $: realCO1 = `${hexToRGB(co1, co1o)} ${co1p}%`;
    $: realCO2 = `${hexToRGB(co2, co2o)} ${co2p}%`;

    const modalOC = () => {
        show = !show;
    };

    const grad = (deg, color1, color2, prop) => {
        if (prop === "Linear") {
            return `linear-gradient(${deg}deg, ${color1} , ${color2})`;
        } else {
            return `radial-gradient(circle, ${color1} , ${color2})`;
        }
    };
    $: gradient = grad(deg, realCO1, realCO2, property);

    $: styles = { gradient: `${gradient}` };

    $: cssVarStyles = Object.entries(styles)
        .map(([key, value]) => `--${key}:${value}`)
        .join(";");
    $: css = `
        background: ${gradient};
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
        width: 200px;
        height: 200px;
        background: var(--gradient);
    }
</style>

<Nav />
<Modal text={css} bind:show />
<main style={cssVarStyles}>
    <div class="container">
        <div class="box" />
    </div>
    <Select ops={propList} name="Gradient" bind:value={property} />
    {#if property === 'Linear'}
        <Slider2 min="0" max="360" bind:value={deg} text="Angle" />
    {/if}
    <Color bind:value={co1} text="Color 1" />
    <Slider2
        min="0"
        max="1"
        step="0.1"
        bind:value={co1o}
        text="Color 1 Opacity" />
    <Slider2 min="0" max="200" bind:value={co1p} text="Color 1 Percentage" />
    <Color bind:value={co2} text="Color 2" />
    <Slider2
        min="0"
        max="1"
        step="0.1"
        bind:value={co2o}
        text="Color 2 Opacity" />
    <Slider2 min="0" max="200" bind:value={co2p} text="Color 2 Percentage" />
    <div class="btn">
        <Btn text="CSS!" calc={modalOC} />
    </div>
</main>
