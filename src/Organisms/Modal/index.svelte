<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
</script>

<style>
  .modal-background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.3);
    z-index: 2;
  }

  .modal {
    position: absolute;
    left: 50%;
    top: 50%;
    width: calc(100vw - 4em);
    max-width: 32em;
    transform: translate(-50%, -50%);
    z-index: 2;
  }

  button {
    display: block;
  }
</style>

<div class="modal-background" on:click='{() => dispatch("close")}'></div>

<div class="modal">
  <slot name="header"></slot>
  <slot></slot>
</div>
