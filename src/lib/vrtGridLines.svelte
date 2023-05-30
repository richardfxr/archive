<script lang="ts">
    /* === PROPS ============================== */
    export let aside = false;
</script>



<div class:aside class="gridLines" role="presentation">
    <div class="left"></div>
    <div class="center"></div>
    <div class="right"></div>
</div>



<style lang="scss">
    .gridLines {
        position: absolute;
        inset: 0;
        z-index: 0;

        margin: 0 calc(2 * $border-width);

        & > div {
            // grid lines
            position: absolute;
            top: 0;
            bottom: 0;
            width: $border-width;
            z-index: 0;

            background-color: var(--clr-border-bg);

            &::before {
                // line marks
                content: "";
                position: absolute;
                top: calc($topbar-height + $mark-top + 3 * $border-width);
                width: $border-width;
                height: $mark-size;

                background-color: var(--clr-1000);
            }
        }

        .left {
            left: var(--_inset);
        }

        .center {
            left: calc(50% - $border-width);
        }

        .right {
            right: var(--_inset);
        }
    }



    // === BREAKPOINTS ========================
    @media (min-width: $breakpoint-4col) {
        .gridLines {
            --_inset: calc(25% - 0.5 * #{$border-width});

            &.aside {
                --_inset: 40%;
                
                .left, .right {
                    &::before {
                        display: none;
                    }
                }

                .center {
                    display: none;
                }
            }
        }
    }

    @media (max-width: $breakpoint-4col) {
        .gridLines {
            --_inset: calc(33.333% - 0.5 * #{$border-width});

            .center {
                display: none;
            }
        }
    }

    @media (max-width: $breakpoint-3col) {
        .gridLines {
            .left, .right {
                display: none;
            }

            .center {
                display: block;
            }
        }
    }

    @media (max-width: $breakpoint-stacked) {
        .gridLines {
            .left, .right {
                display: block;
            }
        }
    }

    @media (max-width: $breakpoint-2col) {
        .gridLines {
            .left, .right {
                display: none;
            }
        }
    }

    @media (max-width: $breakpoint-1col) {
        .gridLines {
            .center {
                display: none;
            }
        }
    }
</style>