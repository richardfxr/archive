<script lang="ts">
    /* === IMPORTS ============================ */
    import VrtGridLines from "$lib/vrtGridLines.svelte";
</script>



<header class="header">
    <VrtGridLines aside />

    <div class="main">
        <div class="text">
            <h1>Archive</h1>
            
            <p>The complete collection of Richard Fu's work.</p>
        </div>

        <div class="quicksettings">
            <div class="placeholder"></div>
            <div class="placeholder"></div>
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
        position: relative;
        z-index: 1;

        background-color: var(--clr-bg);
        padding: var(--pad-sm) 0;
        border: $border var(--clr-border-main);
        margin: $border-gap;

        &::before, &::after {
            // top line marks
            content: "";
            position: absolute;
            top: $mark-top;
            width: $border-width;
            height: $mark-size;

            background-color: var(--clr-1000);

            animation: squareSlideFromRight var(--_animation-duration) 0.3s var(--_animation-easing) 1;
            animation-fill-mode: backwards;
        }

        &::before {
            // top left line mark
            left: -$border-width;
        }

        &::after {
            // top right line mark
            right: -$border-width;
        }
    }

    .text {
        // internal variables
        --_square-size: 6px;
        --_animation-duration: 0.18s;
        --_animation-easing: cubic-bezier(.16,.25,.4,1.01);

        padding: var(--pad-border);
        border-top: $border var(--clr-border-main);

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

        border-top: $border var(--clr-border-main);
        border-bottom: $border var(--clr-border-main);
        margin-left: auto;

        .placeholder {
            width: var(--input-size);
            height: var(--input-size);
            border-left: $border var(--clr-border-main);
        }
    }

    .bottomText {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        position: relative;

        padding: var(--pad-2xs) var(--pad-xs);

        &::before, &::after {
            // top and bottom border
            content: "";
            position: absolute;
            right: $border-protrusion;
            left: $border-protrusion;
            height: $border-width;

            background-color: var(--clr-border-bg);
        }

        &::before {
            top: 0;
        }

        &::after {
            bottom: 0;
        }
    }



    // === BREAKPOINTS ========================
    @media (min-width: $breakpoint-stacked) {
        .header {
            border-right: $border var(--clr-border-bg);
        }
    }

    // === KEYFRAMES ==========================
    @keyframes squareSlideFromRight {
        from {
            opacity: 0;
            transform: translateX(80px);
        }

        to {
            opacity: 1;
            transform: translateX(0px);
        }
    }

    @keyframes squareSlideFromLeft {
        from {
            opacity: 0;
            transform: translateX(-80px);
        }

        to {
            opacity: 1;
            transform: translateX(0px);
        }
    }

    @keyframes h1SlideFromRight {
        from {
            transform: translateX(100%);
        }

        to {
            transform: translateX(0%);
        }
    }

    @keyframes versionSlideFromRight {
        from {
            opacity: 0;
            transform: translateX(100%);
        }

        to {
            opacity: 1;
            transform: translateX(0%);
        }
    }

    @keyframes pFadeIn {
        from {
            opacity: 0;
        }

        to {
            opacity: 1;
        }
    }
</style>