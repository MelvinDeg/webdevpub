<script>
    import Spinner from "./Spinner.svelte";
    import Results from "./Results.svelte";
    import Search from "./Search.svelte";
    import { promise } from "./stores.js";
    import SpinnerNew from "./Spinner_new.svelte"
</script>

<main>
    <Search />

    {#await $promise}
        <SpinnerNew />
    {:then result}
        <Results json={result} />
    {:catch error}
        <p style="color: red">{error.message}</p>
        
    {/await}
</main>

<style>
    :global(body) {
        padding: 0;
        margin: 0; 
    }

    main {
        height: 100vh;
        width: 100vw;
        background: linear-gradient(to bottom, #2473ab 0%, #1e528e 70%, #5b7983 100%);
        display: flex;
        justify-content: start;
        align-items: center;
        flex-direction: column;
        padding: 0;
        box-sizing: border-box;
    }

    @keyframes gradient {
        0% {
            background-position: 0% 50%;
        }
        50% {
            background-position: 100% 50%;
        }
        100% {
            background-position: 0% 50%;
        }
    }
</style>
