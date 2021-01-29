<template>
  <div class="home">
    <AdvertisingCarousel />
    <div class="container">
      <h3>Top Products</h3>
      <ProductList :list="products" />
    </div>
  </div>
</template>

<script>
import AdvertisingCarousel from '../components/AdvertisingCarousel.vue'
import { mapState } from 'vuex'
import ProductList from '../components/ProductList.vue'
export default {
  name: 'Home',
  components: {
    AdvertisingCarousel,
    ProductList
  },
  computed: {
    ...mapState(['products'])
  }
}
</script>
, ProductItem
