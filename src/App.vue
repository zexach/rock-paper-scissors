<script setup>
  import { ref } from 'vue';
  import Rules from './components/Rules.vue';
  
  const showRules = ref(false)
  const score = ref(10)
  const choices = ['rock','paper','scissors']
  const isPaperPick = ref(false)
  const isRockPick = ref(false)
  const isScissorsPick = ref(false)
  const myPick = ref('')
  const opponentPick = ref('')
  const result = ref('')

  const paperPick = () => {
    isPaperPick.value = true
    myPick.value = choices[1]
  }

  const scissorsPick = () => {
    isScissorsPick.value = true
    myPick.value = choices[2]
  }

  const rockPick = () => {
    isRockPick.value = true
    myPick.value = choices[0]
  }

  const randomCompPick = () => {
    opponentPick.value = choices[Math.floor(Math.random() * choices.length)]
    console.log(opponentPick.value)
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

</script>

<template>
  <div class="container">
    <Rules v-if="showRules" />
    <div class="header">
      <p class="game-name">FLI FLAJ FLUS</p>
      <div class="score-content">
        <p class="score-text">SCORE</p>
        <h2 class="score-value">{{score}}</h2>
      </div>
    </div>
    <div class="rock-paper-scissors">
      <div @click="paperPick(), randomCompPick(), getResult()" class="circle paper">
        <img src="./img/icon-paper.svg" alt="">
      </div>
      <div @click="scissorsPick(), randomCompPick(), getResult()" class="circle scissors">
      <img src="./img/icon-scissors.svg" alt="">
      </div>
      <div @click="rockPick(), randomCompPick(), getResult()" class="circle rock">
        <img src="./img/icon-rock.svg" alt="">
      </div>
    </div>
    <div class="rules">
      <h1>{{result}}</h1>
      <h6>{{opponentPick}}</h6>
      <button @click="showRules = !showRules">{{showRules ? 'CLOSE RULES' : 'RULES'}}</button>
    </div>
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
   .header{
    width: 80%;
    padding: 5px 15px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    border:  2px solid rgb(208, 208, 208);
    border-radius: 5px;
   }
   .game-name{
    width: 10%;
    line-height: 17px;
    font-size: 20px;
    font-weight: 600;
   }
   .score-content{
    padding: 5px 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 5px;
    color: black;
    background-color: white;
   }
   .score-text{
    font-weight: 500;
   }
   .score-value{
    font-size: 30px;
    font-weight: 700;
   }
   .rock-paper-scissors{
    width: 100%;
    height: 400px;
    display: flex; 
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
   }
   .circle{
    width: 130px;
    height: 130px;
    margin: 25px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    background-color: rgb(235, 235, 235);
    cursor: pointer;
    transition: 0.4s;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
   }
   .circle:hover{
    width: 140px;
    height: 140px;
   }
   .rock{
    border: 10px solid rgb(246, 67, 67)
   }
   .paper{
    border: 10px solid rgb(30, 189, 216)
   }
   .scissors{
    border: 10px solid rgb(251, 188, 52)
  }
  .hidden{
    display: none;
  }
   .rules{
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
   }
   button{
    width: 25%;
    padding: 10px;
    background-color: transparent;
    border: 1px solid rgb(208, 208, 208);
    border-radius: 5px;
    color: white;
    cursor: pointer;
    transition: 0.4s;
   }
   button:hover{
    width: 30%;
    background-color: white;
    color: black
   }
</style>
