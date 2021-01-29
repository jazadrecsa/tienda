<template>
  <div>
    <nav class="navbar navbar-light bg-white">
      <div class="container-fluid">
        <router-link to="/" class="navbar-brand">
          <img alt="jeonjang logo" src="../assets/logo.png" />
        </router-link>
        <div class="d-flex">
          <div class="row">
            <div class="col-auto allCenter">
              <label>Iniciar sesión</label>
            </div>
            <div class="col-auto">
              <button
                @click="showCarPreview = true"
                type="button"
                class="btn btn-light position-relative"
              >
                <label><i class="bi bi-cart-fill"></i></label>
                <span
                  class="position-absolute top-0 start-100 translate-middle badge border border-light rounded-circle bg-danger p-2"
                  >{{ carList.length }}<span class="visually-hidden"></span
                ></span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <car-preview :show="showCarPreview" :close="closeCarPreview" />
  </div>
</template>

<script>
import CarPreview from './CarPreview.vue'
import { mapState } from 'vuex'

export default {
  components: { CarPreview },
  computed: {
    ...mapState(['carList'])
  },
  data () {
    return {
      showCarPreview: false
    }
  },
  methods: {
    closeCarPreview () {
      this.showCarPreview = false
    }
  }
}
</script>

<style scoped>
img {
  height: 50px;
}
i {
  font-size: x-large;
}
label {
  font-weight: bold;
}
</style>
