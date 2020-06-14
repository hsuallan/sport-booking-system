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
        <div class="parent" v-on:step-change="alert('a')">
          <div class="div1">
            <stepper :step="step" />
          </div>
          <div class="div2">
            <router-view></router-view>
          </div>
        </div>
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
      step: 3
    }
  }
}
</script>
<style scoped>
.parent {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(4, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}

.div1 {
  grid-area: 1 / 1 / 5 / 2;
}
.div2 {
  grid-area: 1 / 2 / 4 / 6;
}
</style>
