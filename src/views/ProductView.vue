<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col-sm-12 col-md-4 allCenter">
        <img class="img-fluid w-75" :src="product.image" :alt="name" />
      </div>
      <div class="col-sm-12 col-md-4">
        <h3>{{ product.name }}</h3>
        <h5 class="product__brand mt-3">Marca: {{ product.brand }}</h5>
        <div class="row">
          <div class="col-sm-12 col-md-6">
            <stars-review :qualification="product.qualification" />
            <p></p>
          </div>
          <div class="col-sm-12 col-md-6 allCenter">
            <h2 class="fw-bolder">{{ formatPrice(product.price) }}</h2>
          </div>
        </div>
        <hr />
      </div>
      <div class="col-sm-12 col-md-4 d-flex justify-content-center">
        <car-add :product="product" :carItem="carItem" />
      </div>
    </div>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'
import { formatPrice } from '../../utils/functions'
import CarAdd from '../components/CarAdd.vue'
import StarsReview from '../components/StarsReview.vue'
export default {
  components: { StarsReview, CarAdd },
  computed: {
    ...mapState(['product', 'carItem'])
  },
  methods: {
    ...mapActions(['getProduct']),
    formatPrice
  },
  created () {
    this.getProduct(this.$route.params.id)
  }
}
</script>

<style scoped>
h3 {
  color: black;
}
.product__brand {
  color: gray;
}
</style>
