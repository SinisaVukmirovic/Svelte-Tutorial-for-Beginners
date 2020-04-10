<script>
    export let showModal = false;

    // conditional class for conditional styles
    // let isPromotion = true;

    // props
    export let propsMsg;
    export let isPromotion = false;
    // to pass prop from outside of this component we must export it
    // export let propsMsg = 'Default value';
    // default value can alse be given

    // event modifiers
    // some of the more common ones are:
    // once - makes sure that event can only fire once (removes handler)
    // preventDefault - prevent the default action
    // self - only fires the event if the clicked element is the target
</script>

<!-- === MOCK UP === -->
{#if showModal} 
    <!-- <div class="backdrop" class:promotion={isPromotion} on:click> -->
                                                    <!-- not defining on click event here
                                                    means that we want to "event forward" it
                                                    onto the parent element that is 
                                                    using this components -->
        <div class="backdrop" class:promotion={isPromotion} on:click|self>
                                                                <!-- event modifier -->

        <div class="modal">
            <!-- passing prop from another component -->
            <p>{propsMsg}</p>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        position: fixed;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, .7);
    }

    .modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: coral;
        border: 4px solid #eee;
    }

    .promotion .modal {
        background: crimson;
        border: 4px solid #eee;
    }
</style>