<template>
  <div class="food w-75 container justify-content-center">

    <!-- Header -->
    <div class="row mt-5">
      <div class="col">
        <h3>Daftar <strong>Makanan</strong></h3>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="input-group mb-3">
          <input type="text" class="form-control" v-model="searchFood" placeholder="Nama Menu" aria-label="Nama Menu"
            aria-describedby="button-addon2">
          <button class="btn btn-outline-secondary" type="button" id="button-addon2">
            <b-icon icon="search"></b-icon>
          </button>
        </div>
      </div>
    </div>

    <!-- CardList -->
    <div class="row justify-content-center">
      <div class="col-lg-3 col-md-4 m-1" v-for="food in foodFiltered" :key="food.id">
        <FoodCard :product="food"></FoodCard>
      </div>
    </div>

  </div>
</template>

<script>
import FoodCard from '@/components/FoodCard.vue';
import axios from 'axios';

export default {
  name: 'FoodView',
  components: {
    FoodCard
  },
  data() {
    return {
      foods: [],
      searchFood: "",
    };
  },
  methods: {
    setProducts(data) {
      this.foods = data;
    },
  },
  computed: {
    foodFiltered() {
      return this.foods.filter((item) => {
        return item.nama.match(this.searchFood);
      });
    }
  },
  mounted() {
    axios.get('http://localhost:3000/products')
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log(error));
  }
}
</script>

<style></style>