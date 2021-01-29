<template>
  <div class="card-deck row">
    <div
      class="col-sm-12 col-md-4 col-lg-3 mt-2"
      v-for="item in list"
      :key="item.id"
    >
      <ProductItem
        :name="item.name"
        :description="item.description"
        :price="item.price"
        :image="item.image"
        :id="item.id"
      />
    </div>
  </div>
</template>

<script>
import ProductItem from './ProductItem.vue'
export default {
  components: { ProductItem },
  props: {
    list: {
      type: [],
      default: []
    }
  }
}
</script>

<style></style>
