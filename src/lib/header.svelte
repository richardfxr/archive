<script lang="ts">
    /* === IMPORTS ============================ */
    import VrtGridLines from "$lib/vrtGridLines.svelte";
</script>



<header class="header">
    <VrtGridLines aside />

    <div class="main">
        <div class="mainInner">
            <div class="text">
                <h1>Archive</h1>
                
                <p>The complete collection of Richard Fu's work.</p>
            </div>

            <div class="quicksettings">
                <div class="placeholder"></div>
                <div class="placeholder"></div>
            </div>
        </div>
        
    </div>

    <div class="bottomText">
        <p class="version smallText">v1.0.0-alpha1</p>
        <p class="update smallText"><span class="em">UD</span> 2023-05-29</p>
    </div>
</header>


<style lang="scss">
    .header {
        // internal variables
        --_animation-duration: 0.18s;
        --_animation-easing: cubic-bezier(.16,.25,.4,1.01);

        position: relative;

        padding-top: calc($topbar-height + $border-width);
    }

    .main {
        padding: var(--pad-sm) 0;
    }

    .mainInner {
        border-top: $border var(--clr-border-main);
        border-bottom: $border var(--clr-border-main);
    }

    .text {
        // internal variables
        --_square-size: 6px;
        --_animation-duration: 0.18s;
        --_animation-easing: cubic-bezier(.16,.25,.4,1.01);

        position: relative;
        padding: var(--pad-border);

        h1 {
            font-family: "GeneralSans", sans-serif;
            font-size: 2rem;
            font-weight: 700;
            line-height: 1em;
            text-transform: uppercase;
            color: var(--clr-1000);

            // alignment compensation
            margin-top: -0.2rem;

            animation: h1SlideFromRight 0.35s cubic-bezier(.23,0,.26,1.09) 1;
        }

        p {
            line-height: 1.1em;
            max-width: 20ch;

            margin-top: var(--pad-xs);

            animation: pFadeIn 0.3s 0.35s ease-out 1;
            animation-fill-mode: backwards;
        }
    }   

    .quicksettings {
        display: flex;
        flex-flow: row wrap;
        justify-content: end;
        width: 100%;

        border-top: $border var(--clr-border-main);
        margin-left: auto;

        .placeholder {
            width: var(--input-size);
            height: var(--input-size);
            border-left: $border var(--clr-border-main);
        }
    }



    // === BREAKPOINTS ========================
    @media (min-width: $breakpoint-stacked) {
        .header {
            border-right: $border var(--clr-border-bg);
        }
    }

    @media (max-width: $breakpoint-stacked) {
        .mainInner {
            display: grid;
            grid-template-columns: 1fr 1fr;
            align-items: end;
        }

        .text {
            border-right: $border var(--clr-border-main);
        }
    }

    @media (max-width: $breakpoint-2col) {
        .mainInner {
            display: block;
        }

        .text {
            border-right: none;
        }
    }
</style>