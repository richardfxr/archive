<script lang="ts">
    /* === IMPORTS ============================ */
    import VrtGridLines from "$lib/vrtGridLines.svelte";
    import SearchIcon from "$lib/SVGs/searchIcon.svelte";

    /* === PROPS ============================== */
    export let searchString: string;
    // let selectedCategories:

    /* === BINDINGS =========================== */
    let searchInput: HTMLElement;

    /* === VARIABLES ========================== */
    let showFilters = false;
</script>


<form on:submit|preventDefault class="searchForm">
    <VrtGridLines aside noLineMarks />

    <div class="main">
        <div class="alwaysVisible">
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
            
            <label class="filterCheckbox">
                <input
                    class="visuallyHidden"
                    type="checkbox"
                    bind:checked={showFilters}>
                Filters
            </label>
            
        </div>
        
        {#if showFilters}
            <div class="filters">
                <div class="inner"></div>
            </div>
        {/if}
    </div>
    
    <div class="bottomText">
        <p class="smallText"><span class="em">0</span> filters</p>
        <p class="smallText"><span class="em">0</span> projects</p>
    </div>
</form>


<style lang="scss">
    .searchForm {
        position: sticky;
        top: calc(-1 * var(--pad-2xl) - #{$border-width});
        height: 100%;
        z-index: 1000;

        background-color: var(--clr-bg);
        padding-top: var(--pad-2xl);

        &::before {
            // top grid line
            content: "";
            position: absolute;
            top: calc(var(--pad-2xl) - #{$border-width});
            right: $border-protrusion;
            left: $border-protrusion;
            height: $border-width;

            background-color: var(--clr-border-bg);
        }
    }

    .main {
        max-height: calc(100vh - (0.95rem + 2 * var(--pad-2xs)));
        overflow-y: auto;

        &::before, &::after {
            display: none;
        }
    }

    .searchbar {
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        position: relative;

        color: var(--clr-900);
        padding: 0 var(--pad-border);

        transition: color var(--trans-normal);

        #searchInput {
            display: block;
            flex-grow: 1;

            font-family: "GeneralSans", sans-serif;
            font-size: 1.35rem;
            font-weight: 600;
            line-height: 1em;
            text-transform: uppercase;
            color: inherit;

            padding:
                calc(var(--pad-border) - 0.15rem)
                var(--pad-border)
                var(--pad-border)
                var(--pad-border);

            &::placeholder {
                color: inherit;
            }

            &::-webkit-search-cancel-button {
                -webkit-appearance: none;
            }
        }
    }

    .filterCheckbox{
        display: flex;
        flex-direction: row;
        align-items: center;
        width: 100%;

        font-family: "GeneralSans", sans-serif;
        font-size: 1.1rem;
        font-weight: 500;
        line-height: 1em;
        text-transform: uppercase;
        color: inherit;

        padding: var(--pad-border);

        cursor: pointer;
    }

    .filters {
        background-color: rebeccapurple;

        .inner {
            height: 150vh;
        }
    }

    .bottomText {
        .smallText {
            text-transform: uppercase;
        }
    }



    // === BREAKPOINTS ========================
    @media (min-width: $breakpoint-stacked) {
        .searchForm {
            border-right: $border var(--clr-border-bg);
        }

        .searchbar {
            border-bottom: $border var(--clr-border-main);
        }
    }

    @media (max-width: $breakpoint-stacked) {
        .alwaysVisible {
            display: grid;
            grid-template-columns: 1fr 1fr;
        }

        .searchbar {
            border-right: $border var(--clr-border-main);
            border-bottom: none;
        }
    }

    @media (max-width: $breakpoint-2col) {
        .alwaysVisible {
            display: block;
        }

        .searchbar {
            border-right: none;
            border-bottom: $border var(--clr-border-main);
        }
    }
</style>