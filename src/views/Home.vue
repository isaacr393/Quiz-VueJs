<template>
  <div class="home">
    <div class="content-home">
      <div class="logo-container">
        <div class="center-container">
          <img alt="Not Smart Enough Logo" src="../assets/NotSmart.png" class="logo">
        </div>
      </div>
      <div class="text-container">
        <p>
          This game was specially created let you know how NOT smart you are. So basically don't get
          frustrated with the question that are given and much less with me
        </p>
        <p>This game questions are brought to us thanks to the OPEN TRIVIA API so get mad at them
          for the questions
        </p>
      </div>
      <div class="play-container">
        <div class="btn-play">
          <router-link to="/about">
            <span>Try</span>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: { }
}
</script>

<style scoped>
.home{
  display: flex;
  justify-content: center;
  overflow: hidden;
}
.content-home{
  display: flex;
  flex-direction: column;
  max-width: 70vw;
  min-width: 70vw;
  min-height: 80vh;
  align-items: center;
  overflow: hidden;
}
.logo-container{
  position: relative;
  min-height: 250px;
  width: 100%;
  overflow: hidden;
  display: flex;
  justify-content: center;
}
.center-container{
  position: absolute;
  top: -40%;
  max-height: 40%;
}
.logo{
  width: 100%;
  min-width: 400px;
}
.text-container{
  max-width: 30vw;
}
.text-container > p{
  padding: 15px;
  line-height: 1.5em;
  font-family: 'Roboto', sans-serif;
  color: rgb(3, 3, 3),
}
.play-container{
  width: 100%;
  display: flex;
  justify-content: center;
}
.btn-play{
  font-size: 2em;
  padding: 15px;
  border-radius: 10%;
  border: 0px solid #444;
  font-family: 'Dancing Script', cursive;
  cursor: pointer;
  width: 30%;
  max-width: 100px;
  min-width: 60px;
}
</style>
