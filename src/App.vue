<template>
  <div id="app">
    <Header
      :numCorrect="numCorrect"
      :numTotal="numTotal"
    />

    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox
            v-if="questions.length"
            :currentQuestion="questions[index]"
            :next="next"
            :increment="increment"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from './components/Header'
import QuestionBox from './components/QuestionBox'

export default {
  name: 'App',
  components: {
    Header,
    QuestionBox
  },
  data() {
    return {
      questions: [],
      index: 0,
      numCorrect: 0,
      numTotal: 0
    }
  },
  methods: {
    next() {
      this.index++;
    },
    increment(isCorrect) {
      if(isCorrect) {
        this.numCorrect++;
      }
      this.numTotal++;
    }
  },
  mounted: function() {
    fetch('https://opentdb.com/api.php?amount=10&category=27&difficulty=easy&type=multiple', {
      method: 'get'
    })
      .then((response) => {
        return response;
      })
      .then((jsonData) => {
        //this.questions = jsonData.results;
        console.log(jsonData);
        this.questions = [
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "What is the fastest  land animal?",
                              "correct_answer": "Cheetah",
                              "incorrect_answers": [
                                  "Lion",
                                  "Thomson&rsquo;s Gazelle",
                                  "Pronghorn Antelope"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "What is the scientific name for modern day humans?",
                              "correct_answer": "Homo Sapiens",
                              "incorrect_answers": [
                                  "Homo Ergaster",
                                  "Homo Erectus",
                                  "Homo Neanderthalensis"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "The Kākāpō is a large, flightless, nocturnal parrot native to which country?",
                              "correct_answer": "New Zealand",
                              "incorrect_answers": [
                                  "South Africa",
                                  "Australia",
                                  "Madagascar"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "Hippocampus is the Latin name for which marine creature?",
                              "correct_answer": "Seahorse",
                              "incorrect_answers": [
                                  "Dolphin",
                                  "Whale",
                                  "Octopus"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "How many legs do butterflies have?",
                              "correct_answer": "6",
                              "incorrect_answers": [
                                  "2",
                                  "4",
                                  "0"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "Which class of animals are newts members of?",
                              "correct_answer": "Amphibian",
                              "incorrect_answers": [
                                  "Fish",
                                  "Reptiles",
                                  "Mammals"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "What is the collective noun for a group of crows?",
                              "correct_answer": "Murder",
                              "incorrect_answers": [
                                  "Pack",
                                  "Gaggle",
                                  "Herd"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "By definition, where does an abyssopelagic animal live?",
                              "correct_answer": "At the bottom of the ocean",
                              "incorrect_answers": [
                                  "In the desert",
                                  "On top of a mountain",
                                  "Inside a tree"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "What colour is the female blackbird?",
                              "correct_answer": "Brown",
                              "incorrect_answers": [
                                  "Black",
                                  "White",
                                  "Yellow"
                              ]
                          },
                          {
                              "category": "Animals",
                              "type": "multiple",
                              "difficulty": "easy",
                              "question": "What is the name of a rabbit&#039;s abode?",
                              "correct_answer": "Burrow",
                              "incorrect_answers": [
                                  "Nest",
                                  "Den",
                                  "Dray"
                              ]
                          }
                      ]
      })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
