<template>
  <div class="question" v-if="current == index">
      <div class="question-card">
        <div class="question-header">
            Question  #{{index + 1}}
        </div>
        <div class="question-ask">
                {{ decodeHTMLEntity(question.question) }}
        </div>
        <div class="question-answer">
                <div v-for="answer in answers" :key="answer" class="question-option">
                    <input type="radio" :value="answer" :id="answer+'__'" v-model="answered" class="option-input">
                    <label :for="answer+'__'" class="option-label">{{decodeHTMLEntity(answer)}}</label>
                </div>
        </div>
        <div class="question-footer">
            <button v-if="index < 9" class="btn-finalizar" @click="clickAnswer">
                Siguiente
            </button>
            <button v-else class="btn-finalizar" @click="clickFinish">
                Finalizar
            </button>
            <button v-if="index > 0" class="btn-anterior" @click="clickBack">
                Anterior
            </button>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  props: {
    question: Object,
    index: Number,
    current: Number
  },

  created () {
  },

  computed: {
    answers () {
      let myAns = []
      if (Array.isArray(this.question.incorrect_answers)) {
        myAns = this.question.incorrect_answers
        myAns.push(this.question.correct_answer)
        this.shuffleArray(myAns)
      } else {
        myAns.push('True')
        myAns.push('False')
        this.shuffleArray(myAns)
      }
      return myAns
    }
  },

  data () {
    return {
      loading: false,
      data: null,
      error: null,
      answer: null,
      answered: null
    }
  },

  methods: {
    clickAnswer () {
      if (this.answered === this.question.correct_answer) {
        this.$emit('Done', true)
      } else {
        this.$emit('Done', false)
      }
    },
    clickFinish () {
      if (this.answered === this.question.correct_answer) {
        this.$emit('Finish', true)
      } else {
        this.$emit('Finish', false)
      }
    },
    clickBack () {
      this.$emit('Back', true)
    },
    shuffleArray (array) {
      for (var i = array.length - 1; i > 0; i--) {
        var j = Math.floor(Math.random() * (i + 1))
        var temp = array[i]
        array[i] = array[j]
        array[j] = temp
      }
    },
    decodeHTMLEntity (text) {
      const element = document.createElement('textarea')
      element.innerHTML = text
      return element.value
    }
  }
}
</script>

<style scoped>
.question{
    display: flex;
    flex-direction: column;
    padding: 60px;
    min-width: 100%;
    height: 100%;
    border: 0px solid red;
    align-items: center;
}
.question-card{
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px 40px;
    width: 20%;
    box-shadow: 0px 0px 5px black;
    height: 50%;
}
.question-header{
    display: flex;
    justify-content: center;
    padding: 15px;
    width: 100%;
    border: 0px solid blue;
    font-size: 2em;
    font-family: 'Roboto', sans-serif;
}
.question-ask{
    display: flex;
    justify-content: center;
    padding: 15px;
    width: 100%;
    border: 0px solid blue;
    font-size: 1.5em;
    font-family: 'Roboto', sans-serif;
}
.question-answer{
    padding: 15px;
    border: 0px solid red;
    width: 100%;
    display: flex;
    flex-direction: column;
}
.question-option{
    border: 0px solid green;
    padding: 15px;
    display: flex;
}
.option-input{
    width: 2em;
    line-height: 2em;
    font-size: 2em;
    height           : 0.875em;
    border           : 0.0625em solid rgb(192,192,192);
    border-radius    : 0.25em;
}
.option-label{
    font-size: 1.2em;
    font-family: 'Roboto', sans-serif;
}
.question-footer{
    padding: 15px;
    border: 0px solid pink;
    width: 100%;
    display: flex;
    justify-content: space-evenly;
}
.btn-finalizar{
    background: rgb(216, 220, 223);
    padding: 15px;
    border-radius: 15%;
    font-family: 'Dancing Script', cursive;
    font-size: 1.5em;
    border: 1px solid #333;
}
.btn-anterior{
    background: rgb(179, 155, 155);
    padding: 15px;
    border-radius: 15%;
    font-family: 'Dancing Script', cursive;
    font-size: 1.5em;
}
</style>
