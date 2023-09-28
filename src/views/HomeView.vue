<template>
  <div class="home w-75 container justify-content-center">

    <!-- Hero -->
    <div class="container">
      <div class="row">
        <div class="col-md-6 order-md-2">
          <div class="d-flex justify-content-center align-items-center p-3">
            <img src="../assets/img/ilustrasi.png" alt="Illustration" class="img-fluid" width="85%">
          </div>
        </div>
        <div class="col-md-6 order-md-1 mt-md-0 mt-sm-3 mt-3">
          <div class="d-flex justify-content-center h-100">
            <div class="align-self-center">
              <h2>Delicious Food Menu, <br>in Your Gadget</h2>
              <p>Ayo segera pilih dan pesan makananmu</p>
              <b-button variant="success" class="btn-order" href="/food">
                <b-icon-arrow-right></b-icon-arrow-right> Pesan
              </b-button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Best Food -->
    <div class="container my-5">
      <div class="row justify-content-center my-3">
        <div class="col-6">
          <h3>Best Food</h3>
        </div>
        <div class="d-flex col-2 justify-content-end">
          <b-button variant="success" class="btn-order" href="/food">
            <b-icon-arrow-right></b-icon-arrow-right> Pesan
          </b-button>
        </div>
      </div>

      <div class="row justify-content-center my-3">
        <div class="col-lg-3 col-sm-4 mx-1 mt-5" v-for="product in products" :key="product.id">
          <FoodCard :product="product"></FoodCard>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import FoodCard from '@/components/FoodCard.vue'
import axios from 'axios';

export default {
  name: 'HomeView',
  components: {
    FoodCard
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    }
  },
  mounted() {
    axios.get('http://localhost:3000/products')
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log(error));
  }
}
</script>
