<script>
    import Navbar from "./navbar/navbar.svelte";
    import Sidebar from "./navbar/sidebar.svelte";
    let open = false;
</script>

<Sidebar bind:open />
<Navbar bind:sidebar={open} />
