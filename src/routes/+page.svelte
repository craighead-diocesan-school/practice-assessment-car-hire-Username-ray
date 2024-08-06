<script>
  import Header from "$lib/Header.svelte"
  import { onMount } from "svelte"
  import Card from "$lib/Card.svelte"

  let cars = []
  let availableCars = []
  let loading = true
  let error = null
  let cart = []
  let cartLimit = 3
  const apiUrl = "https://digitech.craighead.school.nz/api/car-hire"

  onMount(async () => {
    try {
      const response = await fetch(apiUrl)
      const data = await response.json()
      cars = [...data.fast, ...data.nice]
      availableCars = cars.filter((car) => car.available)
    } catch (e) {
      error = "Error. Failed to fetch car data."
    } finally {
      loading = false
    }
  })

  function addToCart(car) {
    if (cart.length >= cartLimit) {
      alert("You can add only up to 3 cars to your cart.")
      return
    }
    cart = [...cart, car]
  }

  function totalCost() {
    return cart.reduce((total, car) => total + car.price, 0)
  }
</script>

<Header />

<main>
  {#if loading}
    <div>Loading...</div>
  {:else if error}
    <div>{error}</div>
  {:else if availableCars.length === 0}
    <div>Out of stock, no available cars.</div>
  {:else}
    <div class="car-list">
      {#each availableCars as car}
        <Card {car} on:addToCart={() => addToCart(car)} />
      {/each}
    </div>
  {/if}

  <h2>Your Cart</h2>
  {#if cart.length === 0}
    <div>Your cart is empty.</div>
  {:else}
    <div class="cart">
      {#each cart as car}
        <Card {car} />
      {/each}
    </div>
    <div>Total Cost: ${totalCost()}</div>
  {/if}
</main>

<footer>
  <p>&copy; Craighead Diocesan School 2024</p>
</footer>

<style>
  .car-list,
  .cart {
    margin: 20px;
  }
</style>
