<template>
  <div id="app">
    <v-app id="inspire">
      <v-app-bar app color="cyan" dark>
        <v-toolbar-title>運動中心預約系統</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn color="purple" @click="$router.replace('/');step = 1">
          <v-icon left>mdi-book</v-icon>預約
        </v-btn>
        <v-btn class="ma-4" color="purple" @click="$router.replace('/query');step = 1">
          <v-icon left>mdi-information-outline</v-icon>查詢
        </v-btn>
      </v-app-bar>
      <v-content fluid>
        <v-row justify="center">
         <v-col lg="6" sm="12"><stepper :step="step" /></v-col>
        </v-row>
        <v-row justify="center">
          <v-col lg="8" sm="12"><router-view v-on:step-change="stepChange"></router-view></v-col>
        </v-row>
      </v-content>
      <v-footer color="cyan" app>
        <v-spacer></v-spacer>
        <span class="white--text">&copy; 2020</span>
      </v-footer>
    </v-app>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import stepper from './components/stepper'
export default {
  name: 'App',

  components: {
    // HelloWorld
    stepper
  },
  data () {
    return {
      step: 1
    }
  },
  methods: {
    stepChange: function (newStep) {
      // new
      this.step = newStep
    }
  }
}
</script>
