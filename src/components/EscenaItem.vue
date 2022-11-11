<template>
    <div>
      <!--level 1 code:
        <p>{{ msg }}</p>
      -->
      <ul>
        <li 
          v-for="(frase, index) in sentencesArray"
          :key="index"
          :class="{ active: index === sentenceNumber}"
          >
          {{ frase }}
        </li>
      </ul>
    </div>
  </template>
  
  
  <script>
  export default {
    name: 'EscenaItem',
    props: {
      sentencesArray: [],
      sentenceNumber: Number,
    },
    data(){
      return {
        /*level 1 code:
        msg: "El nostre heroi estava surant per l'espai sideral quan a la llunyania va albirar una nau espacial",
        */
      }
    },
  }
  </script>
  

  <style scoped lang="scss">
    div {
  
      & ul {
        list-style: none;
        padding: 0;
        
        & li {
          text-align: center;
          font-size: small;
          margin: 10px;
          padding: 10px;
          border: 2px solid black;
          border-radius: 20px;
        }
      }
    }

    .active {
      background-color: pink;
    }
  </style>
  