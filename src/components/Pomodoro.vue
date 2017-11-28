<template>
  <v-container fluid>
    <v-layout row wrap>
        <v-flex xs12 lg12 class="text-xs-center  text-sm-center text-lg-center">
            <v-btn href="#" @click="startPomodoro" large class="primary" v-text="buttonText" ></v-btn>
            <v-btn href="#" @click="resetPomodoro" large class="primary">Reset Pomodoro</v-btn>
        </v-flex>
    </v-layout>

    <v-layout row wrap>
        <v-flex xs6 md6 lg6 class="text-lg-right text-md-right text-xs-right">
            <p  class="display-4" v-text="minutes"></p>   
        </v-flex>
        <v-flex xs6 md6 lg6 class="text-lg-left text-md-left text-xs-left">
            <p class="display-4" v-text="showSeconds"></p>        
        </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      inicioPomodoro: true,
      minutes: 25,
      seconds: 0,
      interval: null,
      started: false
    }
  },
  methods: {
    resetPomodoro () {
      this.minutes = 25
      this.seconds = 0
      clearInterval(this.interval)
      this.started = false
    },
    startPomodoro () {
      if (this.started) {
        this.started = false
      } else {
        if (!this.minutes && !this.seconds) this.resetTimer()
        this.started = true
        this.interval = setInterval(this.intervalCallback, 1000)
      }
    },
    intervalCallback  () {
      if (!this.started) return false
      if (this.seconds === 0) {
        if (this.minutes === 0) {
          this.timerComplete()
          return null
        }
        this.seconds = 59
        this.minutes--
      } else {
        this.seconds--
      }
    },
    timerComplete () {
      this.started = false
      alert('Bom trabalho! Tire um descanço de 5 Minutos')
    }
  },
  computed: {
    buttonText () {
      if (this.started) return 'Parar'
      return 'Iniciar'
    },
    showSeconds () {
      if (this.seconds < 10) {
        return ':' + '0' + parseInt(this.seconds, 10)
      }
      return ':' + this.seconds
    }
  }
}
</script>

<style>

</style>
