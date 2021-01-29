<template>
  <div v-if="show">
    <main class="position-absolute top-0 end-0 bg-light border shadow-sm">
      <div class="container">
        <h2>Carrito</h2>
        <section>
          <card-list />
        </section>

        <div class="row mt-5">
          <div class="col">
            <h4>Total:</h4>
          </div>
          <div class="col-auto d-flex justify-content-end">
            <h4 class="pr-3">{{ formatPrice(total) }}</h4>
          </div>
        </div>
        <div class="row">
          <div class="col-md-6 col-sm-12">
            <button
              @click="close"
              class="btn btn-dark w-100 shadow-sm"
              type="button"
            >
              Seguir comprando
            </button>
          </div>
          <div class="col-md-6 col-sm-12">
            <button class="btn  btn-warning w-100 shadow-sm" type="button">
              Proceder al pago
            </button>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import CardList from './CardList.vue'
import { mapState, mapActions } from 'vuex'
import { formatPrice } from '../../utils/functions'

export default {
  components: { CardList },
  props: {
    show: {
      type: Boolean,
      default: false
    },
    close: Function
  },
  computed: {
    ...mapState(['total'])
  },
  methods: {
    ...mapActions(['getTotal']),
    formatPrice
  },
  created () {
    this.getTotal()
  }
}
</script>

<style scoped>
main {
  z-index: 2;
  position: absolute;
  height: 100vh;
  max-width: 450px;
  min-width: 250px;
}
section {
  max-height: 75vh;
  overflow-x: hidden;
  overflow-y: auto;
}
h4 {
  font-weight: bolder;
}
</style>
