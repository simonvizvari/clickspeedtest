<template>
  <div class="content">
    <div class="main">
      <h1 class="score">Your CPS Test Score: {{ score }}</h1>
      <h1 style="margin-left: 40%;"><strong>Timer: {{ timerCount }}s</strong></h1>
      <button v-if="!secondButton"  @click="this.secondButton = true, startTimer()"><h1>Click here to start</h1></button>
      <button v-if="secondButton" @click="score++"><h1>Click here to start</h1></button>
    </div>

    <div v-if="timerCount <= 0" class="tabulka">
      <div class="text-content">
        <div @click="timerCount+= 5, secondButton = false, score = 0" style="margin-left: auto; color: black; font-size: 25px; cursor: pointer; padding-right: 10px">x</div>
        <img v-if="(score/5) < 5" class="picture" src="https://t2.gstatic.com/licensed-image?q=tbn:ANd9GcSQ0vQ0fQvRZloilSoCObNMBPznznKNG8b7Z6IBuzKHF-qszEz8zaCshcx95vKrzzLb" alt="">
        <img v-else-if="(score/5) >= 5 && (score/5) < 8" class="picture" src="https://assets.petco.com/petco/image/upload/f_auto,q_auto/rabbit-care-sheet" alt="">
        <img v-else-if="(score/5) >= 8 && (score/5) < 12" class="picture" src="https://assets.newatlas.com/dims4/default/8384671/2147483647/strip/true/crop/6144x4096+0+0/resize/2880x1920!/quality/90/?url=http%3A%2F%2Fnewatlas-brightspot.s3.amazonaws.com%2Fa2%2F52%2F735143314703a075587fa2445de4%2Fdepositphotos-644018666-xl.jpg" alt="">
        <img v-else-if="(score/5) >= 12" class="picture" src="https://www.pascalmaranus.com/assets/media/photos/pairi-daiza/fallback/_PDZ4840.jpg" alt="">
        <h1>
          Youre a 
          <strong>
            <span v-if="(score/5) < 5">turtle</span>
            <span v-else-if="(score/5) >= 5 && (score/5) < 8 ">rabbit</span>
            <span v-else-if="(score/5) >= 8 && (score/5) < 12">octopus</span>
            <span v-else-if="(score/5) >= 12">cheetah</span>
          </strong>!
        </h1> 
        <p>Well.. You Clicked with the speed of {{ score / 5 }}CPS</p>
        <p>You made {{ score }} clicks in 5 seconds</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      score: 0,
      timerCount: 5,
      animal: 'turtle',
      secondButton: false,
    }
  },
  methods: {
    startTimer() {
      if(this.timerCount > 0) {
        setTimeout(() => {
          this.timerCount -= 1
          this.startTimer()
        }, 1000)
      }
    },
  }
}
</script>

<style>
* {
  user-select: none;
}
.content {
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}
.main {
  flex-direction: column-reverse;
}
.tabulka {
  position: absolute;
  height: 70vh;
  width: 45vw;
  background: #cacaca;
  border-radius: 20px;
}
button {
  height: 250px;
  width: 500px;
}
.score {
  font-size: 50px;
}
.text-content {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 0;
  color: white;
}
.picture {
  margin-top: 50px;
  height: 150px;
  width: 150px;
  border-radius: 50%;
}
</style>