<template>
    <div>
        <h1 v-if="!mostrar">
          Tutorial d'empresa
        </h1>
        <p v-if="!mostrar">
          A continuació veuràs una sèrie de consells, 
          per avançar o retrocedir fes-ho a través dels botons.
        </p>
        <BotonsItem 
          v-if="mostrar" 
          @select-item="selectItem">
        </BotonsItem>
        <EscenaItem 
          v-if="mostrar" 
          :sentencesArray="storyArray"
          :sentenceNumber="currentSentence">
        </EscenaItem>
        <button @click="showAndStartFinish">
          {{ btnText }}
        </button>
    </div>
  </template>


  <script>
  import EscenaItem from './EscenaItem.vue'
  import BotonsItem from './BotonsItem.vue'
  import json from '../assets/historyArray.json'

  export default {
    name: 'HomeItem',
    props: {
      json: [],
    },
    components: {
      EscenaItem,
      BotonsItem,
    },
    data(){
      return {
        storyArray: json,
        currentSentence: 0,
        mostrar: false,
        btnText: 'Començar',
      }
    },
    methods: {
      selectItem(operator) {
            if (operator === 'prev') {
                if (this.currentSentence > 0) {
                    this.currentSentence--;
                }
            }
            if (operator === 'next') {
                if (this.currentSentence < 3) {
                    this.currentSentence++;
                }
            }
        },
        showAndStartFinish() {
          this.mostrar = !this.mostrar;
          this.currentSentence = 0;
          this.mostrar ? 
            this.btnText = 'Tornar' 
            : this.btnText = 'Començar';
        }
    }
  }
  </script>
  

  <style scoped lang="scss">
   *{
    text-align: center;
   }
    button {
      margin: 20px;
      padding: 10px;
      border-radius: 20px;
    }

  </style>