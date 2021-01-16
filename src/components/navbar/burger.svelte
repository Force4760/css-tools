<script>
    export let open = false;
</script>

<style>
    svg {
        min-height: 24px;
        transition: transform 0.3s ease-in-out;
    }

    svg line {
        stroke: white;
        stroke-width: 3;
        transition: transform 0.3s ease-in-out;
        cursor: pointer;
    }

    div {
        z-index: 60;
        color: white;
        margin-right: 16px;
        border: none;
        margin-bottom: 0px;
    }

    .open {
        transform: scale(0.7);
    }

    .open #top {
        transform: translate(6px, 0px) rotate(45deg);
    }

    .open #middle {
        opacity: 0;
    }

    .open #bottom {
        transform: translate(-12px, 9px) rotate(-45deg);
    }
</style>

<div on:click={() => (open = !open)}>
    <svg class:open width="32" height="24">
        <line id="top" x1="0" y1="2" x2="32" y2="2" />
        <line id="middle" x1="0" y1="12" x2="32" y2="12" />
        <line id="bottom" x1="0" y1="22" x2="32" y2="22" />
    </svg>
</div>
