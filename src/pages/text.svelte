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
    let text = "Hello";
    let text2 = "World";
    let tal = "center";
    const talOps = ["left", "center", "right", "justify"];

    let tdec = "none";
    const tdecOps = ["overline", "underline", "line-through", "none"];

    let ttra = "none";
    const ttraOps = ["capitalize", "uppercase", "lowercase", "none"];

    let ws = "normal";
    const wsOps = ["normal", "no-wrap", "pre", "pre-line", "pre-wrap"];
    let ww = "normal";
    const wwOps = ["normal", "break-word"];

    let letSpace = 0;
    let tcol = "#ffffff";
    let top = 1;
    let fsize = 32;
    let lheight = 1.5;
    let tin = 0;
    let wspace = 10;
    let fwe = 400;
    $: realTcol = hexToRGB(tcol, top);
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
        letSpace: `${letSpace}px`,
        fsize: `${fsize}px`,
        lheight: `${lheight}`,
        tin: `${tin}px`,
        wspace: `${wspace}px`,
        fwe: `${fwe}`,
        tal: `${tal}`,
        tdec: `${tdec}`,
        ttra: `${ttra}`,
        ws: `${ws}`,
        ww: `${ww}`,
        realTcol: `${realTcol}`,
    };

    $: cssVarStyles = Object.entries(styles)
        .map(([key, value]) => `--${key}:${value}`)
        .join(";");
    $: css = `
        color: ${realTcol};
        font-size: ${fsize};
        font-weight: ${fwe};
        letter-spacing: ${letSpace};
        line-height: ${lheight};
        text-indent: ${tin};
        text-align: ${tal};
        text-decoration: ${tdec};
        text-transform: ${ttra};
        word-spacing: ${wspace};
        word-wrap: ${ww};
        white-space: ${ws};
    `;

    const modalOC = () => {
        show = !show;
    };
</script>

<Nav />
<Modal text={css} bind:show />
<main style={cssVarStyles}>
    <div class="container">
        <p class="text">{text}<br />{text2}</p>
    </div>
    <Input bind:value={text} name="Text" />
    <Input bind:value={text2} name="Text 2" />
    <Slider2 min="-10" max="100" bind:value={letSpace} text="Letter Spacing" />
    <Slider2 min="0" max="100" bind:value={fsize} text="Font Size" />
    <Slider2
        min="300"
        max="900"
        step="100"
        bind:value={fwe}
        text="Font Weight"
    />

    <Slider2
        min="0"
        max="10"
        step="0.1"
        bind:value={lheight}
        text="Line Height"
    />
    <Select ops={talOps} name="Text Align" bind:value={tal} />
    <Select ops={tdecOps} name="Text Decoration" bind:value={tdec} />
    <Select ops={ttraOps} name="Text Transform" bind:value={ttra} />
    <Slider2 min="0" max="100" bind:value={tin} text="Text Indent" />
    <Select ops={wsOps} name="White Space" bind:value={ws} />
    <Slider2 min="0" max="100" bind:value={wspace} text="Word Spacing" />
    <Select ops={wwOps} name="Word Wrap" bind:value={ww} />
    <Color bind:value={tcol} text="Color" />
    <Slider2 min="0" max="1" step="0.01" bind:value={top} text="Opacity" />
    <div class="btn">
        <Btn text="CSS!" calc={modalOC} />
    </div>
</main>

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
    .text {
        color: var(--realTcol);
        font-size: var(--fsize);
        font-weight: var(--fwe);
        letter-spacing: var(--letSpace);
        line-height: var(--lheight);
        text-indent: var(--tin);
        text-align: var(--tal);
        text-decoration: var(--tdec);
        text-transform: var(--ttra);
        word-spacing: var(--wspace);
        word-wrap: var(--ww);
        white-space: var(--ws);
    }
</style>
