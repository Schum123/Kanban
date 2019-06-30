<script>
  import FormText from "../../Molecules/FormText/index.svelte";
  import FormSelect from "../../Molecules/FormSelect/index.svelte";
  import AddButton from "../../Atoms/Button/index.svelte";
  export let valueFirstName
  export let valueLastName
  export let valueEmail
  export let valueAddress
  export let valueAge
  export let selected
  export let disabled
</script>
<div>
    <h3>Lägg till användare</h3>
    <fieldset>
        <FormText id="firstname" name="firstname" type="text" placeholder="Joe" text="Förnamn" bind:value={valueFirstName}/>
        <FormText id="lastname" name="lastname" type="text" placeholder="Doe" text="Efternamn" bind:value={valueLastName}/>
        <FormText id="age" name="age" type="text" placeholder="25" text="Ålder" bind:value={valueAge}/>
        <FormText id="email" name="email" type="email" placeholder="Joe.doe@example.com" text="Email" bind:value={valueEmail}/>
        <FormText id="address" name="address" type="text" placeholder="Adress 123" text="Adress" bind:value={valueAddress}/>
        <FormSelect text="Status" bind:selected/>
    </fieldset>
    <div class="submit--row">
        <input type="submit" value="Lägg till" on:click disabled={disabled}>
    </div>
</div>

<style>
    div:not(.submit--row) {
        background-color: var(--colorLight);
        max-width: 645px;
        padding: 10px 18px 20px 24px;
        border-radius: 4px;
    }
    h3 {
        color: #424770;
        font-size: 20px;
        margin: 10px 0 30px 0;
        font-weight: bold;
    }

    input[type="submit"] {
        white-space: nowrap;
        display: inline-block;
        height: 40px;
        line-height: 40px;
        padding: 0 14px;
        box-shadow: 0 4px 6px rgba(50, 50, 93, 0.11), 0 1px 3px rgba(0, 0, 0, 0.08);
        border-radius: 4px;
        font-size: 15px;
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.025em;
        color: var(--colorLight);
        background: #6772e5;
        text-decoration: none;
        transition: all 0.15s ease;
        border: none;
        cursor: pointer;
    }
    input[type="submit"]:hover {
        transform: translateY(-1px);
        box-shadow: 0 13px 27px -5px rgba(50,50,93,.25), 0 8px 16px -8px rgba(0,0,0,.3), 0 -6px 16px -6px rgba(0,0,0,.025);
        box-shadow: 0 7px 14px rgba(50,50,93,.1), 0 3px 6px rgba(0,0,0,.08);
    }
    input[type="submit"]:disabled {
        background-color: #2425338c;
        cursor: no-drop;
    }
    input[type="submit"]:disabled:hover {
       transform: none;
       box-shadow: none;
    }
    .submit--row {
        padding: 12px 0 0;
        display: flex;
        justify-content: flex-end;
    }
</style>
