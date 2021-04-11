<template>
  <div class="about">
    <div class="loading" v-if="loading">Loading...</div>
    <div class="error" v-if="error">{{error}}</div>
    <div class="container">
      <question v-for="(question, index) in data" :key="question.correct_answer"
      :question="question" :index="index" :current="current"
      @Done="Answered"
      @Finish="Finish"
      @Back="Back"
      />
    </div>
  </div>
</template>

<script>
import Question from '../components/Question.vue'
export default {
  components: {
    Question
  },

  created () {
    this.fetchData()
  },

  data () {
    return {
      loading: false,
      data: null,
      error: null,
      current: 0,
      results: []
    }
  },

  methods: {
    fetchData () {
      this.loading = true
      this.$axios.get('https://opentdb.com/api.php?amount=10')
        .then(response => {
          this.data = response.data.results
          console.log(this.data)
          this.loading = false
        })
        .catch(e => {
          this.error = e.response
          this.loading = false
        })
    },

    Answered (correct) {
      if (correct) {
        this.results[this.current] = true
      } else {
        this.results[this.current] = false
      }
      this.current += 1
    },

    Finish (correct) {
      if (correct) {
        this.results[this.current] = true
      } else {
        this.results[this.current] = false
      }
      this.current += 1
      this.$router.push({ name: 'Results', params: { results: this.results } })
    },

    Back () {
      this.current -= 1
    }
  }
}
</script>

<style scoped>
.container{
  width: 100%;
  height: 80%;
  display: flex;
  justify-content: center;
  border: 0px solid red;
}
</style>
