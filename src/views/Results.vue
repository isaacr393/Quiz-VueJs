<template>
  <div>
      <div class="result">
          <div class="result-card">
              <div class="result-header">
                  <h1>These are your results</h1>
              </div>
              <div class="result-content">
                  {{corrects}} good answer out of {{amount}}
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
  props: {
    results: Array
  },

  data () {
    return {
      amount: 0,
      corrects: 0
    }
  },

  mounted () {
    this.corrects = this.sumScore()
  },

  methods: {
    sumScore () {
      this.amount = this.results.length
      let correct = 0 / this.amount
      correct = 0
      this.results.forEach(val => {
        if (val) {
          correct++
        }
      })
      return correct
    }
  }
}
</script>

<style>
.result{
    display: flex;
    flex-direction: column;
    padding: 60px;
    min-width: 100%;
    height: 100%;
    border: 0px solid red;
    align-items: center;
}
.result-card{
    width: 30%;
    height: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    box-shadow: 0px 0px 5px black;
}
.result-header{
    line-height: 1.5em;
    font-family: 'Roboto', sans-serif;
    color: rgb(3, 3, 3);
    padding: 40px;
    border-bottom: 1px solid #666;
}
.result-content{
    line-height: 1.5em;
    font-family: 'Roboto', sans-serif;
    color: rgb(3, 3, 3);
    padding: 40px;
}
</style>
