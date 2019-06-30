<script>
  export let selected;

  let selectValues = [
    {
      value: "1",
      text: "Kontakt"
    },
    {
      value: "2",
      text: "Dialog"
    },
    {
      value: "3",
      text: "Intervju"
    },
    {
      value: "4",
      text: "Erbjudande"
    },
    {
      value: "5",
      text: "Avslutad"
    }
  ];
</script>

<select bind:value="{selected}">
  <option selected>Välj status</option>
  {#each selectValues as val}
  <option value="{val.value}">
    {val.text}
  </option>
  {/each}
</select>

<style>
  * {
    width: 100%;
    border: none;
    background-color: #f6f9fc;
    padding: 9px 20px 9px 13px;
    font-weight: 400;
    font-size: 17px;
  }
</style>
