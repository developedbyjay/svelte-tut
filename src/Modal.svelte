
<script>
  // Props
  export let showModal;
  export let isPromo;

  function handleClick() {
    // showModal = !showModal;
    isPromo = !isPromo;
  }
</script>

<!-- The modal component -->
{#if showModal}
  <div>
    <div class="backdrop" class:promo={isPromo} on:click|self on:keydown on:keyup on:keypress>
      <div class="modal">
        <slot></slot>
      </div>
    </div>
  </div>
{/if}

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.8);
  }

  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background-color: #fff;
  }


  .promo .modal {
    background-color: crimson;
  }
</style>
