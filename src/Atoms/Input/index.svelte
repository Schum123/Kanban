<script>
  export let id;
  export let name;
  export let type;
  export let placeholder;
  export let value
</script>

<input id="{id}" name="{name}" type="text" placeholder="{placeholder}" bind:value />

<style>
  * {
    display: block;
    background-color: #f6f9fc;
    border: none;
    outline: none;
    width: 100%;
    border-radius: 4px;
    color: #32325d;
    font-weight: 400;
    font-size: 17px;
    line-height: 26px;
    padding: 5px 20px 8px 13px;
    transition: background-color 0.1s ease-in, color 0.1s ease-in;
  }
</style>
