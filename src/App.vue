<script setup>
  import { ref } from 'vue';
  import Header from './components/Header.vue';
  import Score from './components/Score.vue';
  import Rules from './components/Rules.vue';
  import Choice from './components/Choice.vue';
  import OpponentPick from './components/OpponentPick.vue';
  import Result from './components/Result.vue';
  
  const showRules = ref(false)
  const score = ref(0)
  const choices = ['rock','paper','scissors']
  const isPaperPick = ref(true)
  const isRockPick = ref(true)
  const isScissorsPick = ref(true)
  const myPick = ref('')
  const opponentPick = ref('')
  const result = ref('')

  const paperPick = () => {
    isScissorsPick.value = false
    isRockPick.value = false
    myPick.value = choices[1]
  }

  const scissorsPick = () => {
    isPaperPick.value = false
    isRockPick.value = false
    myPick.value = choices[2]
  }

  const rockPick = () => {
    isScissorsPick.value = false
    isPaperPick.value = false
    myPick.value = choices[0]
  }

  const randomCompPick = () => {
    opponentPick.value = choices[Math.floor(Math.random() * choices.length)]
  }

  
  const getResult = () => {
    switch(myPick.value){
      case 'rock':
        if(opponentPick.value === 'rock') result.value = 'DRAW'
        else if(opponentPick.value === 'paper'){
          result.value = 'YOU LOST'
          score.value -= 1
        } else {
          result.value = 'YOU WIN'
          score.value += 1
        }
        break
      case 'paper':
        if(opponentPick.value === 'paper') result.value = 'DRAW'
        else if(opponentPick.value === 'scissors'){
          result.value = 'YOU LOST'
          score.value -= 1
        } else {
          result.value = 'YOU WIN'
          score.value += 1
        }
        break
      case 'scissors':
        if(opponentPick.value === 'scissors') result.value = 'DRAW'
        else if(opponentPick.value === 'rock'){
          result.value = 'YOU LOST'
          score.value -= 1
        } else {
          result.value = 'YOU WIN'
          score.value += 1
        }
        break
      }
    }
    
  const resetRound = () => {
    myPick.value = null
    opponentPick.value = null
    isPaperPick.value = true
    isScissorsPick.value = true
    isRockPick.value = true
  }

  </script>

<template>
  <div class="container">
    <Rules v-if="showRules" />
    <Header name="FLI FLAJ FLUS" />
    <Score :score="score" />
    <div class="rock-paper-scissors">
      <h3 v-if="!isPaperPick || !isScissorsPick || !isRockPick">YOUR PICK</h3>
      <div class="first-row">
        <Choice
          choice="https://i.imgur.com/B9bhcFt.png" 
          @click="paperPick(), randomCompPick(), getResult()"
          :class="{'hidden': !isPaperPick}"
          style="border: 15px solid #2ce014"
        />
        <Choice
          choice="https://i.imgur.com/hYMBReL.png"
          @click="scissorsPick(), randomCompPick(), getResult()"
          :class="{'hidden': !isScissorsPick}"
          style="border: 15px solid red"
        />
      </div>
      <Choice
        choice="https://i.imgur.com/o41ORt9.png"
        @click="rockPick(), randomCompPick(), getResult()"
        :class="{'hidden': !isRockPick}"
        style="border: 15px solid #ffd70d"
      />
    </div>
    <OpponentPick :opponentPick="opponentPick" v-if="!isPaperPick || !isScissorsPick || !isRockPick" />
    <Result :result="result" v-if="myPick != null" />
    <button class="result-btn" v-if="!isPaperPick || !isScissorsPick || !isRockPick" @click="resetRound">PLAY AGAIN</button>
    <button @click="showRules = !showRules">{{showRules ? 'CLOSE RULES' : 'RULES'}}</button>
  </div>
</template>

<style scoped>
  .container{
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    position: relative;
  }
  .rock-paper-scissors{
    width: 100%;
    min-height: 200px;
    display: flex; 
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }
  .first-row{
    display: flex;
    flex-direction: row;
  }
  .result-btn{
    width: 200px;
    padding: 15px;
    background-color: white;
    border: 1px solid rgb(208, 208, 208);
    border-radius: 5px;
    color: black;
    font-size: 18px;
    font-weight: 600;
    cursor: pointer;
    transition: 0.4s;
  }
  .result-btn:hover{
    background-color: transparent;
    color: white;
  }

   h3{
    font-weight: 700;
   }

  .hidden{
    display: none;
  } 
  button{
    width: 120px;
    padding: 10px;
    background-color: transparent;
    border: 1px solid rgb(208, 208, 208);
    border-radius: 5px;
    color: white;
    cursor: pointer;
    transition: 0.4s;
    font-weight: 600;
  }
  button:hover{
    background-color: white;
    color: black
  }
</style>
