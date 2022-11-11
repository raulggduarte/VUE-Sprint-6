<template>
    <div>
        <BotonsItem @select-item="selectItem"></BotonsItem>
        <EscenaItem :sentencesArray="storyArray" :sentenceNumber="currentSentence"></EscenaItem>
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
        }
    }
  }
  </script>
  

  <style scoped lang="scss">

  </style>