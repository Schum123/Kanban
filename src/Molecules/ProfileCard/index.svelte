<script>
  export let name;
  export let imgSrc;
  export let age;
  export let email;
  export let address;
</script>

<div class="card">
  <img src="{imgSrc}" class="img img-responsive" />
  <h3 class="name">{name}</h3>
  <div class="wrap">
    <div class="info">
      <label>Ålder</label>
      <span>{age}</span>
    </div>
    <div class="info">
      <label>Email</label>
      <span>{email}</span>
    </div>
    <div class="info">
      <label>Adress</label>
      <span>{address}</span>
    </div>
  </div>
</div>

<style>
  .card {
    max-width: 300px;
    background-color: var(--colorLight);
    border-radius: 5px;
    box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    position: relative;
    margin: 10px auto;
    padding: 50px 15px 25px 15px;
  }
  .card:before {
    content: "";
    position: absolute;
    top: -60px;
    right: 0px;
    left: 0px;
    height: 170px;
    background-color: #7ebdfb;
    transform: skewY(-20deg);
  }
  .card img {
    height: 100px;
    width: 100px;
    object-fit: cover;
    margin: 10px auto;
    border-radius: 50%;
    transition: all linear 0.25s;
    position: relative;
  }

  .card .name {
    padding-top: 15px;
    font-weight: bold;
    color: #333;
    text-transform: capitalize;
    font-size: 21px;
  }

  .card .info {
    color: #333;
    margin-bottom: 5px;
  }
  label,
  span {
    display: block;
    text-align: left;
  }
  span {
    font-weight: bold;
  }

  .wrap {
    display: flex;
    flex-wrap: wrap;
    margin-left: 20px;
    margin-top: 30px;
  }
  .wrap * {
    flex-basis: 50%;
  }
</style>
