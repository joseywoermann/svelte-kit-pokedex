<script>
    import Nav from "../components/Nav.svelte";
</script>

<body class="p-8 max-w-6xl mx-auto">
    <Nav/>
    <slot></slot>
</body>

<style>
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
</style>