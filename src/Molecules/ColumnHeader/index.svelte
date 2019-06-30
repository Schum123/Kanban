<script>
  import Text from "../../Atoms/Heading/index.svelte";
  export let text
</script>
<div aria-label="Test column heading" class="board__column--header">
    <Text text={text} />
</div>

<style>
    * {
        border-radius: 4px;
        margin-bottom: 10px;
        position: relative;
        height: 70px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    *:first-child{
        background-color: #43458b;
    }
</style>