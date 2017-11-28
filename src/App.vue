<template>
  <v-app dark>  
    <v-toolbar app class="primary " >
      <v-toolbar-title class="text-xs-center  text-sm-center text-lg-center">Pomodoro PWA</v-toolbar-title>
    </v-toolbar>
    <main>
      <router-view></router-view>
    </main>
    <v-footer app>
      <span >&copy; 2017 Developed by Armando Alan</span>
    </v-footer>
  </v-app>

</template>

<script>
  export default {
    data () {
      return {
      }
    }
  }
</script>
