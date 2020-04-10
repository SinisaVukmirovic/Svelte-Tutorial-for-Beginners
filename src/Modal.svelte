<script>
    export let showModal = false;

    // conditional clas for conditional styles
    // let isPromotion = true;

    // props
    export let propsMsg;
    export let isPromotion = false;
    // to pass prop from outside of this component we must export it
    // export let propsMsg = 'Default value';
    // default value can alse be given
</script>

<!-- === MOCK UP === -->
{#if showModal}
    <div class="backdrop" class:promotion={isPromotion} on:click>
                                                    <!-- not defining on click event here
                                                    means that we want to "event forward" it
                                                    onto the parent element that is 
                                                    using this components -->
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
    }

    .promotion .modal {
        background: crimson;
    }
</style>