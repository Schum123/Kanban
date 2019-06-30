<script>
  import ColumnHeader from "../../Molecules/ColumnHeader/index.svelte";
  import AddUser from "../../Atoms/Button/index.svelte";

  export let text
  export let accessor

</script>
<li class="board__column">
    <ColumnHeader text={text}/>
    <ul id="{accessor}">
        <slot></slot>
    </ul>
    <AddUser text="Lägg till" on:click/>
</li>

<style>
    ul {
        min-height: 5px;
    }
</style>