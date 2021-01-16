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

    let property;
    const propList = ["Box", "Margin", "Padding", "Border", "Box Shadow"];
    const styleList = [
        "dotted",
        "dashed",
        "solid",
        "double",
        "groove",
        "ridge",
        "inset",
        "outset",
        "none",
        "hidden",
    ];

    //box
    let boxbc = "#4d194d";
    let boxc = "#fff";
    let boxw = 200;
    let boxh = 200;
    let text = "Hello";

    //margin
    let mart = 0;
    let marr = 0;
    let marb = 50;
    let marl = 0;

    //padding
    let boxpt = 0;
    let boxpr = 0;
    let boxpb = 0;
    let boxpl = 0;

    //border
    let bostyle = "solid";
    let boc = "#000000";
    let bow = 0;
    let brtl = 0;
    let brtr = 0;
    let brbr = 0;
    let brbl = 0;

    //box shadow
    let bsh = 0;
    let bsv = 0;
    let bsb = 0;
    let bss = 0;
    let bsc = "#000000";
    let bso = 1;
    $: realBsc = hexToRGB(bsc, bso);
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

    $: styles = {
        boxbc: `${boxbc}`,
        boxc: `${boxc}`,
        boxpt: `${boxpt}px`,
        boxpr: `${boxpr}px`,
        boxpb: `${boxpb}px`,
        boxpl: `${boxpl}px`,
        boxw: `${boxw}px`,
        boxh: `${boxh}px`,

        brtl: `${brtl}px`,
        brtr: `${brtr}px`,
        brbr: `${brbr}px`,
        brbl: `${brbl}px`,
        bsh: `${bsh}px`,
        bsv: `${bsv}px`,
        bsb: `${bsb}px`,
        bss: `${bss}px`,
        bsc: `${realBsc}`,
        bow: `${bow}px`,
        boc: `${boc}`,
        bostyle: `${bostyle}`,
        mart: `${mart}px`,
        marr: `${marr}px`,
        marb: `${marb}px`,
        marl: `${marl}px`,
    };

    $: cssVarStyles = Object.entries(styles)
        .map(([key, value]) => `--${key}:${value}`)
        .join(";");
    $: css = `
            height: ${boxh}px;
            width: ${boxw}px;
            padding: ${boxpt}px ${boxpr}px ${boxpb}px ${boxpl}px;
            background-color: ${boxbc};
            color: ${boxc};
            margin: ${mart}px ${marr}px ${marb}px ${marl}px;
            border-top-left-radius: ${brtl}px;
            border-top-right-radius: ${brtr}px;
            border-bottom-right-radius: ${brbr}px;
            border-bottom-left-radius: ${brbl}px;
            box-shadow: ${bsh}px ${bsv}px ${bsb}px ${bss}px ${bsc};
            border: ${bow}px ${bostyle} ${boc};
    `;

    const modalOC = () => {
        show = !show;
    };
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
        height: var(--boxh);
        width: var(--boxw);
        text-align: left;
        padding: var(--boxpt) var(--boxpr) var(--boxpb) var(--boxpl);
        background-color: var(--boxbc);
        color: var(--boxc);
        margin: var(--mart) var(--marr) var(--marb) var(--marl);
        border-top-left-radius: var(--brtl);
        border-top-right-radius: var(--brtr);
        border-bottom-right-radius: var(--brbr);
        border-bottom-left-radius: var(--brbl);
        box-shadow: var(--bsh) var(--bsv) var(--bsb) var(--bss) var(--bsc);
        border: var(--bow) var(--bostyle) var(--boc);
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>

<Nav />
<Modal text={css} bind:show />
<main style={cssVarStyles}>
    <div class="container">
        <div class="box">{text}</div>
    </div>
    <Select ops={propList} name="Property" bind:value={property} />

    {#if property === 'Box'}
        <Input bind:value={text} name="Text" />
        <Slider2 bind:value={boxw} text="Box Width" min="1" max="200" />
        <Slider2 bind:value={boxh} text="Box Height" min="1" max="200" />
        <Color bind:value={boxbc} text="Box (Background Color)" />
        <Color bind:value={boxc} text="Box (Foreground Color)" />
    {:else if property === 'Margin'}
        <Slider bind:value={mart} text="Margin (Top)" />
        <Slider bind:value={marr} text="Margin (Right)" />
        <Slider bind:value={marb} text="Margin (Bottom)" />
        <Slider bind:value={marl} text="Margin (Left)" />
    {:else if property === 'Padding'}
        <Slider bind:value={boxpt} text="Padding (Top)" />
        <Slider bind:value={boxpr} text="Padding (Right)" />
        <Slider bind:value={boxpb} text="Padding (Bottom)" />
        <Slider bind:value={boxpl} text="Padding (Left)" />
    {:else if property === 'Border'}
        <Slider bind:value={bow} text="Border (Width)" />
        <Color bind:value={boc} text="Border (Color)" />
        <Select ops={styleList} name="Border (Style)" bind:value={bostyle} />
        <Slider bind:value={brtl} text="Border Radius (Top Left)" />
        <Slider bind:value={brtr} text="Border Radius (Top Right)" />
        <Slider bind:value={brbr} text="Border Radius (Bottom Right)" />
        <Slider bind:value={brbl} text="Border Radius (Bottom Left)" />
    {:else if property === 'Box Shadow'}
        <Slider bind:value={bsh} text="Box Shadow (Horizontal Lenght)" />
        <Slider bind:value={bsv} text="Box Shadow (Vertical Lenght)" />
        <Slider bind:value={bsb} text="Box Shadow (Blur Radius)" />
        <Slider bind:value={bss} text="Box Shadow (Spread Radius)" />
        <Slider2
            bind:value={bso}
            text="Box Shadow (Opacity)"
            min="0"
            max="1"
            step="0.1" />
        <Color bind:value={bsc} text="Box Shadow (Color)" />
    {/if}
    <div class="btn">
        <Btn text="CSS!" calc={modalOC} />
    </div>
</main>
