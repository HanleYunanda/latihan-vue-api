<template>
  <div class="card">
    <img :src="require(`@/assets/img/foods/${product.gambar}`)" class="card-img-top" :alt="product.gambar">
  <div class="card-body">
    <h5 class="card-title">{{ product.nama }}</h5>
    <p class="card-text">{{ product.harga }}</p>
    <a href="#" class="btn btn-primary">Pesan</a>
  </div>
</div>
</template>

<script>
export default {
    name: 'FoodCard',
    props: ['product']
}
</script>

<style>

</style>