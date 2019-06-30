<script>
  import Modal from '../../Organisms/Modal/index.svelte'
  import Card from '../../Molecules/ProfileCard/index.svelte'

  export let fullName = "";
  export let imgSrc
  export let age
  export let email
  export let address
  export let showModalInfoUser = false
  let showMenu = false

  function Toggle(){
    showMenu = !showMenu;
  }
  function moreInfo() {
    showModalInfoUser = true
    showMenu = false
  }
</script>

<li class="drag-item">
  <div class="more" on:click="{Toggle}" />
  <ul class="menu" class:active="{showMenu}">
    <li>
      <span on:click={moreInfo}>Visa mer</span>
      <span>Editera</span>
      <span on:click style="color: rgb(255, 109, 109);">Ta bort</span>
    </li>
  </ul>
  <h4>{fullName}</h4>
</li>

{#if showModalInfoUser}
	<Modal on:close="{() => showModalInfoUser = false}">
          <Card name={fullName} imgSrc={imgSrc} age={age} email={email} address={address}/>
	</Modal>
{/if}

<style>
  .menu {
    position: absolute;
    top: 25px;
    display: none;
    width: calc(100% - 25px);
    z-index: 1;
  }
  .menu.active {
    display: block;
  }
  .menu li span {
    color: #000;
    display: block;
    cursor: pointer;
    padding: 5px 12px;
    margin: 0 -12px;
  }
  .menu li span:hover {
    background-color: rgba(0, 0, 0, 0.02);
  }
  ul:not(.menu) {
    min-height: 50px;
  }
  li:not(.menu) {
    border-radius: 4px;
    box-shadow: 0 2px 5px -1px rgba(50, 50, 93, 0.25),
      0 1px 3px -1px rgba(0, 0, 0, 0.3);
    background: #fff;
    padding: 12px;
    text-align: left;
    position: relative;
  }
  h4 {
    color: #000;
    text-transform: capitalize;
  }
  .more {
    position: relative;
    height: 20px;
    width: 25px;
    display: inline;
    float: right;
    cursor: pointer;
  }
  .more:after {
    content: "\2807";
    font-size: 29px;
    position: absolute;
    top: -23px;
    right: 0;
    color: rgba(72, 71, 71, 0.88);
    transform: rotate(-90deg);
  }
</style>
