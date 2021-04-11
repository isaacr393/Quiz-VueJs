<template>

<layout>
  <div id="app">
    <component :is="layout"> </component>
    <router-view/>
  </div>
</layout>
</template>

<script>
import Layout from './views/Layout/layout.vue'

export default {
  components: { Layout },

  data () {
    return {
      layout: 'div'
    }
  }
}
</script>
