<template>
  <div class="container">
      <header>
          <header-nav></header-nav>
      </header>
      <main class="content">
          <slot></slot>
      </main>
      <footer>
            <footer-app></footer-app>
      </footer>
  </div>
</template>

<script>

import HeaderNav from '@/views/Layout/header.vue'
import FooterApp from '@/views/Layout/footer.vue'

export default {
  name: 'layout',
  components: {
    HeaderNav,
    FooterApp
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@100&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Roboto:wght@300&display=swap');
*{
    margin:0;
    padding: 0;
    background-color: rgb(253, 253, 253);
}
header{
    width: 100vw;
}
.content{
    max-width: 100vw;
    overflow: hidden;
    margin-top: 4em;
    margin-bottom: 4em;
}
</style>
