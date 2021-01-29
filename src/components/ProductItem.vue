<template>
  <div class="card" @click="openView">
    <img class="card-img-top card-img img-fluid" :src="image" :alt="name" />
    <div class="card-img-overlay d-flex justify-content-end p-1">
      <button type="button" class="btn btn-light rounded-circle allCenter">
        <span class="bi bi-heart-fill pb-1"></span>
      </button>
    </div>
    <div class="card-body">
      <h5 class="card-title text-truncate">{{ name }}</h5>
      <p class="card-text text-truncate">
        {{ description }}
      </p>
      <h3>{{ formatPrice(price) }}</h3>
    </div>
  </div>
</template>

<script>
import { formatPrice } from '../../utils/functions'
import router from '../router'

export default {
  data () {
    return {
      showModal: false
    }
  },
  components: {},
  props: {
    id: Number,
    name: String,
    description: String,
    price: Number,
    image: String
  },
  computed: {},
  methods: {
    formatPrice,
    openView () {
      const productId = this.id
      router.push({ name: 'ProductView', params: { id: productId } })
    }
  }
}
</script>

<style scoped>
button {
  height: 30px;
  width: 30px;
}
img {
  height: 240px;
}

i {
  font-size: large;
}
div:hover {
  cursor: pointer;
}
</style>
