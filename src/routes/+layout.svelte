<script lang="ts">
    /* === IMPORTS ============================ */
    import Header from "$lib/header.svelte";
</script>

<div class="fullWidth">
    <div class="wrapper">
        <Header />

        <div class="content">
            <main id="main">
                <slot></slot>
            </main>
        </div>
    </div>
</div>



<style lang="scss">
    .fullWidth {
        position: relative;
    }

    .wrapper {
        max-width: var(--maxWidth);
    }

    .content {
        min-height: 100vh;

        padding: var(--pad-border);

        #main {
            height: 200vh;
        }
    }

    @media (min-width: $breakpoint-smtablet) {
        .fullWidth {
            padding: 0 var(--pad-border);

            &::before {
                // full width topbar line
                content: "";
                position: absolute;
                top: var(--topbar-height);
                right: 0;
                left: 0;

                height: var(--border-width);
        
                background-color: var(--clr-blue-200);
            }
        }

        .wrapper {
            display: grid;
            grid-template-columns: var(--sidebar-width) minmax(0, 1fr);
            grid-template-rows: auto 1fr;
            grid-template-areas:
                "header content"
                "filters content";
            align-items: start;

            border-right: var(--border) var(--clr-blue-200);
            border-left: var(--border) var(--clr-blue-200);
            margin: 0 auto;
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
            border-left: var(--border) var(--clr-blue-200);
        }
    }

    @media (max-width: $breakpoint-smtablet) {
        .content {
            padding-left: calc(var(--pad-border) * 0.5);
        }
    }
</style>