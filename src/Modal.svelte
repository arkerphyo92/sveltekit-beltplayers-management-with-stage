<script>
    export let showModal = false;
    export let isPromo = false;
    export let message = "Hello Kitty";



    
</script>

{#if showModal}
    <div class="backdrop" class:promo={isPromo} on:click|self>
        <div class="modal">
            <slot></slot>
        </div>
    </div>
{/if}

<style>

</style>