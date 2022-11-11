<template>
  <div id="main" :style="image">
    <h1 v-if="!mostrar">
      Tutorial d'empresa
    </h1>
    <p v-if="!mostrar">
      A continuació veuràs una sèrie de consells,
      per avançar o retrocedir fes-ho a través dels botons.
    </p>
    <BotonsItem v-if="mostrar" @select-item="selectItem">
    </BotonsItem>
    <EscenaItem v-if="mostrar" 
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
import * as storyJs from '../assets/historyArray2.js'

export default {
  name: 'HomeItem',
  components: {
    EscenaItem,
    BotonsItem,
  },
  data() {
    return {
      storyArray: storyJs.storyArray,
      currentSentence: 0,
      mostrar: false,
      btnText: 'Començar',
      image: undefined,
    }
  },
  methods: {
    selectItem(operator) {
      if (operator === 'prev') {
        if (this.currentSentence > 0) {
          this.currentSentence--;
          this.getImage();
        }
      }
      if (operator === 'next') {
        if (this.currentSentence < 3) {
          this.currentSentence++;
          this.getImage();
        }
      }
    },
    showAndStartFinish() {
      this.mostrar = !this.mostrar;
      this.currentSentence = 0;
      this.mostrar ?
        this.btnText = 'Tornar'
        : this.btnText = 'Començar';
      (this.image === undefined) ? 
        this.getImage() 
        : this.image = undefined;
    },
    getImage() {
      this.image = { backgroundImage: 
        `url(${require(`@/assets/img/${
          this.currentSentence + 1
        }.jpg`)})` }
    }

  }
}
</script>
  

<style scoped lang="scss">
* {
  text-align: center;
}

#main {
  padding: 10px;
  background-size: cover;
  background-repeat: no-repeat;
  height: 60vw;
}

button {
  margin: 20px;
  padding: 10px;
  border-radius: 20px;
}
</style>