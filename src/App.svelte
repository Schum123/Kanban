<script>
  import fakeData from '../Helpers/persons.js'
  import Column from "./Organisms/Column/index.svelte"
  import ColumnItem from "./Molecules/ColumnItem/index.svelte"
  import Action from "./Atoms/Button/index.svelte"
  import AddUserForm from './Organisms/AddUserForm/index.svelte'
  import Modal from './Organisms/Modal/index.svelte'
  import VButton from './Atoms/Button/index.svelte'
  import VInput from './Atoms/Input/index.svelte'
  import dragula from "dragula";
  import { onMount } from "svelte";
  import { afterUpdate } from 'svelte';

  export let name;
  export let id;
  const USER_SIZE = 10
  let persons = fakeData.results;
  let showModalAddUser = false;
  let showModalInfoUser = false;
  let showModalAllUsers = false;
  let searchString = '';
  let first = '';
  let last = '';
  let age = '';
  let email = '';
  let address = '';
  let status = '';
  let i = 0;
  onMount(() => {
    console.log(persons)

    dragula([
      document.getElementById("Contact"),
      document.getElementById("Dialog"),
      document.getElementById("Interview"),
      document.getElementById("Offer"),
	    document.getElementById("Completed"),
    ])
    // .setOptions('group', {
    //   invalid: (el, handle) => el.classList.contains('modal')
    // })
      .on("drag", el => {
        // add 'is-moving' class to element being dragged
        el.classList.add("is-moving");
      })
      .on("dragend", el => {
        // remove 'is-moving' class from element after dragging has stopped
        el.classList.remove("is-moving");

        // add the 'is-moved' class for 600ms then remove it
        window.setTimeout(() => {
          el.classList.add("is-moved");
          window.setTimeout(() => {
            el.classList.remove("is-moved");
          }, 600);
        }, 100);
      });
  });
  function create() {
    persons = persons.concat({ name:{first, last}, email, location:{street:address}, age, status, picture:{large:"https://randomuser.me/api/portraits/men/24.jpg"} });
    console.log(persons)
		 i = persons.length - 1;
     first = last =  email = address = status = '';
     showModalAddUser = false;
  }
  function remove(e){
    //TODO: Remove item from array...
    e.target.parentElement.parentElement.parentElement.remove()
  }

  $: filteredPeople = searchString
      ? persons.filter(person => {
        const name = `${person.name.first}, ${person.name.last}`;
        return name.toLowerCase().startsWith(searchString.toLowerCase());
      })
    : persons;
</script>
<div class="container">
{#if persons}
<div class="show-user-wrapper">
  <VButton text="Visa alla" on:click="{() => showModalAllUsers = true}"/>
</div>
    <ul class="board">
      <Column text="Kontakt" accessor="Contact" on:click="{() => showModalAddUser = true}">
        {#each persons.filter(person => person.status === '1') as item, i}
          <ColumnItem
          fullName={item.name.first + ' ' + item.name.last}
          imgSrc={item.picture.large}
          age={item.age}
          email={item.email}
          address={item.location.street}
          on:click="{remove}"/>
        {/each}
      </Column>
      <Column text="Dialog" accessor="Dialog" on:click="{() => showModalAddUser = true}">
        {#each persons.filter(person => person.status === '2') as item, i}
          <ColumnItem
           fullName={item.name.first + ' ' + item.name.last}
           imgSrc={item.picture.large}
           age={item.age}
           email={item.email}
           address={item.location.street}
           on:click="{remove}"/>
        {/each}
      </Column>
      <Column text="Intervju" accessor="Interview" on:click="{() => showModalAddUser = true}">
        {#each persons.filter(person => person.status === '3') as item, i}
        <ColumnItem
        fullName={item.name.first + ' ' + item.name.last}
        imgSrc={item.picture.large}
        age={item.age}
        email={item.email}
        address={item.location.street}
        on:click="{remove}"/>
        {/each}
      </Column>
      <Column text="Erbjudande" accessor="Offer" on:click="{() => showModalAddUser = true}">
        {#each persons.filter(person => person.status === '4') as item, i}
        <ColumnItem
        fullName={item.name.first + ' ' + item.name.last}
        imgSrc={item.picture.large}
        age={item.age}
        email={item.email}
        address={item.location.street}
        on:click="{remove}"/>
        {/each}
      </Column>
      <Column text="Avslutad" accessor="Completed" on:click="{() => showModalAddUser = true}">
        {#each persons.filter(person => person.status === '5') as item, i}
        <ColumnItem
        fullName={item.name.first + ' ' + item.name.last}
        imgSrc={item.picture.large}
        age={item.age}
        email={item.email}
        address={item.location.street}
        on:click="{remove}"/>
        {/each}
      </Column>
    </ul>
{:else}
  <!-- <p class="loading">Laddar...</p> -->
{/if}
{#if showModalAddUser}
	<Modal on:close="{() => showModalAddUser = false}">
      <AddUserForm
        bind:valueFirstName={first}
        bind:valueLastName={last} 
        bind:valueAge={age} 
        bind:valueEmail={email} 
        bind:valueAddress={address} 
        bind:selected={status}
        on:click={create}
        disabled="{!first || !last || !email || !address || !status}"
        />
	</Modal>
{/if}

{#if showModalAllUsers}
	<Modal on:close="{() => showModalAllUsers = false}">
    <div class="user__wrapper">
        <h3>Sök efter person</h3>
      <VInput bind:value={searchString} placeholder="Joe Doe" />
      <ul>
      {#each filteredPeople as item, i}
        <li>{item.name.first} {item.name.last}</li>
      {/each}
    </ul>
  </div>
	</Modal>
{/if}
</div>


<style>
  .show-user-wrapper {
    max-width: 150px;
    margin: 10px -10px 10px auto;
  }
  .user__wrapper {
    background-color: #FFF;
    padding: 20px;
    color: #32325d;
    /* backface-visibility: hidden; */
    min-height: 413px;
    border-radius: 4px;
  }
  .user__wrapper ul {
    margin-top: 30px;
    max-height: 240px;
    overflow-y: scroll;
  }
  .user__wrapper ul li{
    padding: 7px 0;
    border-bottom: 1px solid;
  }
  .user__wrapper h3 {
    color: #424770;
    font-size: 20px;
    margin: 10px 0 30px 0;
    font-weight: bold;
  }
</style>