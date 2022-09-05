<template>
  <div>
    <h2 class="text-center main-title">Products</h2>


    <div class="container">
      <div class="row mt-4">
        <div class="col-sm-3" v-for="product in Products">
          <div class="card">
            <img :src="'http://127.0.0.1:8000/assets/images/' + product.image" :key="product.id" class="card-img-top"
              alt="Image" height="250">
            <div class="card-body">
              <h5 class="card-title">{{ product.product_name }}</h5>
              <p class="card-text">Rs. {{ product.product_price }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>


  </div>

</template>

<script>
export default {
  name: 'Products',
  layout: 'Home',
  data() {
    return {
      Products: [],
    }
  },
  methods: {
    getProduct() {
      this.$axios.get('http://127.0.0.1:8000/api/product').then(response => {
        console.log(response.data);
        this.Products = response.data;
      });
    },
  },
  mounted() {
    this.getProduct();
  },
}
</script>

<style scoped>
.main-title {
  text-decoration: underline;
}
</style>