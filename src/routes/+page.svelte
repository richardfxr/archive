<script lang="ts">
    /* === IMPORTS ============================ */
    import Header from "$lib/header.svelte";
</script>



<div class="wrapper">
    <Header />

    <div class="content">
        <main id="main">
            
        </main>
    </div>
</div>



<style lang="scss">
    .wrapper {
        max-width: var(--maxWidth);

        border-right: $border var(--clr-border-bg);
        border-left: $border var(--clr-border-bg);
        margin: 0 auto;
    }

    .content {
        min-height: 100vh;

        padding: var(--pad-border);

        #main {
            height: 200vh;
        }
    }



    // === BREAKPOINTS ========================
    @media (min-width: $breakpoint-stacked) {
        .wrapper {
            display: grid;
            grid-template-rows: auto 1fr;
            grid-template-areas:
                "header content"
                "filters content";
            align-items: start;
            column-gap: var(--pad-xl);
        }

        :global(.header) {
            grid-area: header;
        }

        :global(.searchForm) {
            grid-area: filters;
        }

        .content {
            grid-area: content;

            padding-left: calc(var(--pad-border) * 0.5);
            border-left: $border var(--clr-border-bg);
        }
    }

    @media (max-width: $breakpoint-stacked) {
        .content {
            padding-left: calc(var(--pad-border) * 0.5);
        }
    }

    @media (min-width: $breakpoint-4col) {
        .wrapper {
            grid-template-columns: 1fr 4fr;
        }
    }

    @media (max-width: $breakpoint-4col) {
        .wrapper {
            grid-template-columns: 1fr 3fr;
        }
    }

    @media (max-width: $breakpoint-3col) {
        .wrapper {
            grid-template-columns: 1fr 2fr;
        }
    }
</style>