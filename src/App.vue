<script setup>
  import { ref } from 'vue';
  import Rules from './components/Rules.vue';
  
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
    <div class="header">
      <p class="game-name">FLI FLAJ FLUS</p>
      <div class="score-content">
        <p class="score-text">SCORE</p>
        <h2 class="score-value">{{score}}</h2>
      </div>
    </div>
    <div class="rock-paper-scissors">
      <h3 v-if="!isPaperPick || !isScissorsPick || !isRockPick">YOUR PICK</h3>
      <div @click="paperPick(), randomCompPick(), getResult()" :class="{'hidden': !isPaperPick}" class="circle paper">
        <img src="./img/icon-paper.svg" alt="">
      </div>
      <div @click="scissorsPick(), randomCompPick(), getResult()" :class="{'hidden': !isScissorsPick}" class="circle scissors">
        <img src="./img/icon-scissors.svg" alt="">
      </div>
      <div @click="rockPick(), randomCompPick(), getResult()" :class="{'hidden': !isRockPick}" class="circle rock">
        <img src="./img/icon-rock.svg" alt="">
      </div>
    </div>
    <div v-if="!isPaperPick || !isScissorsPick || !isRockPick" class="opponent-pick">
      <h3>OPPONENT PICK</h3>
      <div v-if="opponentPick === 'paper'" class="circle paper">
        <img src="./img/icon-paper.svg" alt="">
      </div>
      <div v-if="opponentPick === 'scissors'" class="circle scissors">
        <img src="./img/icon-scissors.svg" alt="">
      </div>
      <div v-if="opponentPick === 'rock'" class="circle rock">
        <img src="./img/icon-rock.svg" alt="">
      </div>
    </div>
    <div class="result" v-if="myPick != null">
      <h1 class="result">{{result}}</h1>
      <button class="result-btn" v-if="!isPaperPick || !isScissorsPick || !isRockPick" @click="resetRound">PLAY AGAIN</button>
    </div>
    <div class="rules">
      <button @click="showRules = !showRules">{{showRules ? 'CLOSE RULES' : 'RULES'}}</button>
    </div>
  </div>
</template>

<style scoped>
  .result{
    width: 80%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
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
    min-height: 200px;
    display: flex; 
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
   }
   .result{
    font-size: 30px;
    font-weight: 700;
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
    width: 250px;
    padding: 20px;
    background-color: transparent;
    color: white;
   }
   h3{
    font-weight: 700;
   }
   .circle{
     width: 120px;
     height: 120px;
     margin: 25px 25px;
     display: flex;
     justify-content: center;
     align-items: center;
     border-radius: 50%;
     background-color: rgb(235, 235, 235);
     cursor: pointer;
     transition: 0.3s;
     box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    }
    .opponent-pick{
     display: flex;
     flex-direction: row;
     align-items: center;
    }
    .circle:hover{
    width: 150px;
    height: 150px;
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
    width: 160px;
    background-color: white;
    color: black
   }
</style>
