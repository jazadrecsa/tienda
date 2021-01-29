<template>
  <div class="card w-75">
    <div class="card-body ">
      <h3 class="card-title fw-bolder allCenter">
        {{ formatPrice(product.price) }}
      </h3>
      <h5 :style="colorAvailable">
        {{ product.available ? 'Disponible' : 'Agotado' }}
      </h5>
      <form>
        <div class="mb-3">
          <label for="disabledSelect" class="form-label">Cantidad</label>
          <select
            id="disabledSelect"
            class="form-select"
            v-model="carItem.amount"
          >
            <option v-for="item in product.amount" :key="item" :value="item">{{
              item
            }}</option>
          </select>
        </div>
        <div class="mb-3">
          <label for="disabledSelect" class="form-label">Talla</label>
          <select
            id="disabledSelect"
            class="form-select"
            v-model="carItem.size"
          >
            <option
              v-for="(item, index) in product.sizes"
              :value="item"
              :key="index"
              >{{ item }}</option
            >
          </select>
        </div>
        <div class="mb-3">
          <label for="disabledSelect" class="form-label">Color</label>
          <select
            id="disabledSelect"
            class="form-select"
            v-model="carItem.color"
          >
            <option
              v-for="(item, index) in product.colors"
              :key="index"
              :value="item"
              >{{ item }}</option
            >
          </select>
        </div>
      </form>

      <div class="d-grid gap-2 col-10 mx-auto">
        <button @click="addProductToCar" class="btn btn-warning " type="button">
          <div class="row">
            <div class="col-2 allCenter">
              <i class="bi bi-cart-fill fs-4 allCenter"></i>
            </div>
            <div class="col-10 allCenter">
              Agregar al carrito
            </div>
          </div>
        </button>
        <button class="btn btn-dark" type="button">
          <div class="row">
            <div class="col-2 allCenter">
              <i class="bi bi-arrow-right-circle-fill fs-4 allCenter "></i>
            </div>
            <div class="col-10 allCenter">
              Compar ahora
            </div>
          </div>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from 'vuex'
import { formatPrice } from '../../utils/functions'
const shortid = require('shortid')

export default {
  computed: {
    ...mapState(['carItem']),
    colorAvailable () {
      return this.product.available ? 'color:green' : 'color:#8B0000'
    }
  },
  methods: {
    formatPrice,
    ...mapActions(['beforeAddProduct', 'addProductCar', 'getTotal']),
    addProductToCar () {
      this.carItem.id = shortid.generate()
      this.addProductCar(this.carItem)
      this.getTotal()
    }
  },
  props: {
    product: Object
  },
  created () {
    this.beforeAddProduct(this.product)
  }
}
</script>

<style scoped>
h3 {
  color: #c01212;
  font-weight: bolder;
}

button {
  font-weight: bolder;
}
</style>
