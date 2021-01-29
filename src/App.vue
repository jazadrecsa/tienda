<template>
  <Header />
  <categories />
  <router-view />
</template>

<script>
import Categories from './components/Categories.vue'
import Header from './components/Header'
import { mapActions } from 'vuex'

export default {
  components: {
    Header,
    Categories
  },
  methods: {
    ...mapActions(['cargarLocalStorage'])
  },
  created () {
    this.cargarLocalStorage()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: rgb(31, 31, 31);
}
.allCenter {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
