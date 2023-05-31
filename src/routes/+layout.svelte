<div class="fullWidth">
    <slot></slot>
</div>



<style lang="scss">
    .fullWidth {
        position: relative;
        padding: 0 var(--pad-md);
        
        &::before {
            // full width topbar line
            content: "";
            position: absolute;
            top: $topbar-height;
            right: 0;
            left: 0;

            height: $border-width;
    
            background-color: var(--clr-border-bg);
        }
    }
</style>