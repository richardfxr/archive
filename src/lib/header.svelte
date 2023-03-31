<header class="header">
    <div class="title">
        <div class="text">
            <h1>Archive</h1>
            <span class="version">v1.0.0</span>
            <p>The complete collection of Richard Fu's work.</p>
        </div>

        <div class="quicksettings">
            <div class="placeholder"></div>
            <div class="placeholder"></div>
        </div>
    </div>

    <div class="topbar dates">
        <span>Updated</span>
        <span>2023-03-28</span>
    </div>
</header>


<style lang="scss">
    .header {
        // internal variables
        --_square-size: 6px;
        --_animation-duration: 0.18s;
        --_animation-easing: cubic-bezier(.16,.25,.4,1.01);

        display: flex;
        flex-direction: column;
        gap: var(--pad-3xl);
        position: relative;

        padding-bottom: var(--pad-6xl);

        &::before {
            // bottom left square
            content: "";
            position: absolute;
            bottom: var(--pad-md);
            left: var(--pad-border);
    
            width: var(--_square-size);
            height: var(--_square-size);
    
            background-color: var(--clr-1000);

            animation: squareSlideFromRight var(--_animation-duration) 0.3s var(--_animation-easing) 1;
            animation-fill-mode: backwards;
        }

        &::after {
            // bottom right square
            content: "";
            position: absolute;
            right: var(--pad-border);
            bottom: var(--pad-md);
    
            width: var(--_square-size);
            height: var(--_square-size);
    
            background-color: var(--clr-1000);

            animation: squareSlideFromLeft var(--_animation-duration) 0.4s var(--_animation-easing) 1;
            animation-fill-mode: backwards;
        }
    }

    .title {
        display: flex;
        flex-direction: row;
        gap: var(--pad-xl);

        padding: 0 var(--pad-border);
    }

    .text {
        // internal variables
        --_square-size: 6px;
        --_animation-duration: 0.18s;
        --_animation-easing: cubic-bezier(.16,.25,.4,1.01);

        display: flex;
        flex-direction: column;
        align-items: flex-start;
        overflow: hidden;

        h1 {
            font-family: "GeneralSans", sans-serif;
            font-size: 2rem;
            font-weight: 700;
            line-height: 1em;
            text-transform: uppercase;
            color: var(--clr-1000);

            margin-bottom: var(--pad-xs);

            animation: h1SlideFromRight 0.35s cubic-bezier(.23,0,.26,1.09) 1;
        }

        .version {
            display: block;
            font-weight: 700;
            color: var(--clr-0);
            background-color: var(--clr-1000);

            padding: 0 var(--pad-sm);

            animation: versionSlideFromRight 0.3s 0.15s cubic-bezier(.23,0,.26,1.09) 1;
            animation-fill-mode: backwards;
        }

        p {
            line-height: 1.1em;
            max-width: 20ch;

            margin-top: var(--pad-md);

            animation: pFadeIn 0.3s 0.35s ease-out 1;
            animation-fill-mode: backwards;
        }
    }   

    .quicksettings {
        display: flex;
        flex-flow: row wrap;
        gap: var(--pad-sm);
        justify-content: end;
        margin-left: auto;

        .placeholder {
            width: 30px;
            height: 30px;
            border: 1px solid var(--clr-600);
        }
    }

    .dates {
        // put dates above title text
        order: -1;
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