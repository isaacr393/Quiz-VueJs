<template>
    <div class="footer-container">
        <footer class="footer">
            <span class="text-footer"> This game was Created by Isaac</span>
        </footer>
    </div>
</template>

<script>

export default {
  name: 'footer-app',
  components: {

  }
}
</script>

<style scoped>
.footer-container{
    width: 100%;
    padding: 1em;
    background: transparent;
    position: fixed;
    bottom: 0;
    left: -2em;
}
.footer{
    background: transparent;
    display: flex;
    justify-content: flex-end;
    font-family: 'Montserrat', sans-serif;
    color: rgb(31, 28, 28),
}
</style>
