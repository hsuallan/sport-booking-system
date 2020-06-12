<template>
  <div id="app">
    <v-app id="inspire">
      <v-app-bar app color="cyan" dark>
        <v-toolbar-title>運動中心預約系統</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn color="purple" @click="$router.push('/')">
          <v-icon left>mdi-book</v-icon>預約
        </v-btn>
        <v-btn class="ma-4" color="purple" @click="$router.push('query')">
          <v-icon left>mdi-information-outline</v-icon>查詢
        </v-btn>
      </v-app-bar>

      <v-content fluid>
        <div class="parent">
          <div class="div1">
            <v-stepper v-model="step" vertical>
              <v-stepper-step step="1" :complete="step>1">選擇運動類型</v-stepper-step>
              <v-stepper-content step="1"></v-stepper-content>
              <v-stepper-step step="2" :complete="step>2">選擇日期</v-stepper-step>
              <v-stepper-content step="2"></v-stepper-content>
              <v-stepper-step step="3" :complete="step>3">選擇時段</v-stepper-step>
              <v-stepper-content step="3"></v-stepper-content>
            </v-stepper>
            <v-btn class="ma-4" color="purple" @click="step = step>3?1:++step">
              <v-icon left>mdi-battery-outline</v-icon>++
            </v-btn>
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

export default {
  name: 'App',

  components: {
    // HelloWorld
  },

  data: () => ({
    //
    step: 2
  })
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
