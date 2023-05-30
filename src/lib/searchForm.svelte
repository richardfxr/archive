<script lang="ts">
    /* === IMPORTS ============================ */
    import SearchIcon from "$lib/SVGs/searchIcon.svelte";

    /* === PROPS ============================== */
    export let searchString: string;
    // let selectedCategories:

    /* === BINDINGS =========================== */
    let searchInput: HTMLElement;

    /* === VARIABLES ========================== */
    let showCatAndTag = false;
</script>


<form on:submit|preventDefault class="searchForm">
    <div class="searchbar">
        <label for="searchInput">
            <SearchIcon />
            <span class="visuallyHidden">search</span>
        </label>

        <input
            bind:this={searchInput}
            type="search"
            placeholder="SEARCH ARCHIVE"
            id="searchInput"
            bind:value={searchString}
            autocomplete="off">
    </div>
    
    
    <button class="filtersButton" on:click={() => showCatAndTag = !showCatAndTag}>Filters</button>
    {#if showCatAndTag}
        <div class="filters">
            <div class="inner"></div>
        </div>
    {/if}
</form>


<style lang="scss">
    .searchForm {
        position: sticky;
        top: 0;
        z-index: 1000;
        background-color: var(--clr-bg);
    }

    .searchbar {
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        position: relative;

        color: var(--clr-900);
        padding: 0 var(--pad-border);
        border-top: $border var(--clr-600);

        transition: color var(--trans-normal);

        &:hover, &:focus-within {
            color: var(--clr-1000);
        }

        #searchInput {
            display: block;
            flex-grow: 1;

            font-family: "GeneralSans", sans-serif;
            font-size: 1.5rem;
            font-weight: 600;
            line-height: 1em;
            text-transform: uppercase;
            color: inherit;

            padding:
                calc(var(--pad-sm) - 0.15rem)
                var(--pad-md)
                var(--pad-sm)
                var(--pad-md);

            &::placeholder {
                color: inherit;
            }

            &::-webkit-search-cancel-button {
                -webkit-appearance: none;
            }
        }
    }

    .filtersButton {
        display: block;
        width: 100%;
        background-color: antiquewhite;
    }

    .filters {
        max-height: 80vh;
        background-color: rebeccapurple;

        overflow-y: auto;

        .inner {
            height: 150vh;
        }
    }
</style>