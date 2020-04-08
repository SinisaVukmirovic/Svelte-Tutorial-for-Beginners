<script>
    let showModal = true;

    // conditional clas for conditional styles
    let isPromotion = true;
</script>

<!-- === MOCK UP === -->
{#if showModal}
    <div class="backdrop" class:promotion={isPromotion}>
        <div class="modal">
            <p>Sign Up for offers!</p>
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