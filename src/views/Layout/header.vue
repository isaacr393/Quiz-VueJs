<template>
    <div class="nav-container">
        <nav class="navigation">
            <div class="minified-logo">
                <img src="../../assets/NotSmartMin.png" alt="Not Smart Min" class="myLogo">
            </div>
            <div class="links">
                <router-link to="/">
                    <span class="link-text">Home</span>
                </router-link> |
                <router-link to="Play">
                    <span class="link-text">Play</span>
                </router-link>
            </div>
        </nav>
    </div>
</template>

<script>

export default {
  name: 'header-nav',
  components: {

  }
}
</script>

<style scoped>
*{
    margin: 0;
    padding: 0;
}
.nav-container{
    width: 100%;
    background-color: rgb(255, 255, 255);
    border: 1px solid rgb(44, 42, 42);
    padding: 1em;
    position: fixed;
    top: 0;
    left: -2em;
    overflow: hidden;
    max-height: 2em;
    z-index: 1;
}
.navigation{
    display: flex;
    justify-content: space-between;
}
.link-text{
    font-family: 'Montserrat', sans-serif;
    color: rgb(36, 32, 32),
}
.minified-logo{
    position: relative;
}
.myLogo{
    position: absolute;
    top: -5em;
}
</style>
