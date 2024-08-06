<script>
  export let car
  export let addToCart
</script>

<div class="card">
  <h3>{car.car}</h3>
  <img src={car.img} alt={car.car} />
  <p>{car.description}</p>
  <p>Price per day: ${car.price}</p>
  {#if addToCart}
    <button on:click={addToCart}>Add to Cart</button>
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
  }
  .card img {
    max-width: 100%;
    height: auto;
  }
</style>
