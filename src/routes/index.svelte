<script>
    import { pokemon } from "../stores/pokestore"
    import Card from "../components/Card.svelte"

    let searchTerm = "";
    let filteredPokeman = [];

    // this "function" runs every time a referenced variable changes (here: searchTerm)
    $: {
        if (searchTerm) {
            filteredPokeman = $pokemon.filter((pokeman) => pokeman.name.toLowerCase().includes(searchTerm.toLowerCase()))
        } else {
            filteredPokeman = [...$pokemon]
        }
    }
</script>

<svelte:head>
    <title>Pokedex</title>
</svelte:head>

<body>
    <h1 class="text-4xl text-center my-8 uppercase">Svelte Kit Pokedex</h1>
    <input class="w-full rounded-md text-lg p-4 border-2 border-gray-200" type="text" placeholder="Search Pokemon" bind:value={searchTerm}>

    <div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
        {#each filteredPokeman as pokeman}
            <Card pokeman={pokeman}/>
        {/each}
    </div>
</body>