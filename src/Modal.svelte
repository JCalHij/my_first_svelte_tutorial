<script>
    export let isPromo = false;
    export let showModal = false;
</script>

{#if showModal}
    <div class="backdrop" class:promo={isPromo} on:click|self>
        <div class="modal">
            <slot></slot>
        </div>
    </div>    
{/if}

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background-color: rgba(0, 0, 0, 0.8);
    }

    .promo .modal {
        background-color: crimson;
        color: white;
    }

    .modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background-color: white;
    }
</style>