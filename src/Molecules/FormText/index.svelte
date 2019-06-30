<script>
  import FormInput from "../../Atoms/Input/index.svelte";
  export let id;
  export let name;
  export let type;
  export let placeholder;
  export let text;
  export let value
</script>

<div class="form--row">
    <label class="firstname" for="{name}">{text}</label>
    <FormInput id="{id}" name="{name}" type="{type}" placeholder="{placeholder}" bind:value />
</div>


<style>
    .form--row {
        display: flex;
        border-bottom: none;
        padding: 4px 0;
        max-width: 600px;
        transition: opacity .2s ease-in,height .2s ease-out;
    }
    label {
        display: block;
        transition: color .1s ease-out;
        color: #424770;
        font-size: 17px;
        font-weight: 500;
        letter-spacing: normal;
        line-height: 26px;
        margin-right: 20px;
        align-self: center;
        flex: 32%;
        text-transform: none;
    }
</style>