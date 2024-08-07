<script>
  export let car
  export let addToCart
</script>

<div class="card">
  <h3>{car.car}</h3>
  <img src={car.img} alt={car.car} />
  <p class="description">{car.description}</p>
  <p class="price">Price per day: ${car.price}</p>
  {#if addToCart}
    <button on:click={addToCart}>Add to Cart →</button>
  {/if}
</div>

<style>
  .card {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    margin: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 400px; /* カードの幅を設定 */
  }
  .card img {
    max-width: 100%;
    height: auto;
  }
  button {
    display: block;
    margin: 5%;
    padding: 1rem 3rem;
    font-size: medium;
    font-weight: bold;
    text-decoration: none;
    background: linear-gradient(to top, rgb(5, 130, 174), #27acd9);
    color: #fff;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    -webkit-box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    transition: 0.5s;
  }
  button:hover {
    color: #fff;
    opacity: 0.5;
  }
  h3 {
    font-size: large;
    font-weight: bold;
    margin-top: 3.5%;
    margin-bottom: 3.5%;
    text-shadow: 1px 1px 2px #b5b3b3;
  }
  p {
    text-align: center;
    margin-top: 2%;
  }
  .description {
    color: darkslategray;
  }
  .price {
    color: blue;
  }
</style>
