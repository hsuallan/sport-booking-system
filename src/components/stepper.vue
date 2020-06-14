<template>
  <v-stepper v-bind:value="step" vertical>
    <v-stepper-step step="1" :complete="step > 1">選擇運動類型</v-stepper-step>
    <v-stepper-content step="1"></v-stepper-content>
    <v-stepper-step step="2" :complete="step > 2">選擇日期</v-stepper-step>
    <v-stepper-content step="2"></v-stepper-content>
    <v-stepper-step step="3" :complete="step > 3">選擇時段</v-stepper-step>
    <v-stepper-content step="3"></v-stepper-content>
    <v-stepper-step step="4" :complete="step > 4">填寫資料</v-stepper-step>
    <v-stepper-content step="4"></v-stepper-content>
    <v-stepper-step step="5" :complete="step > 5">成功預約</v-stepper-step>
    <v-stepper-content step="5"></v-stepper-content>
  </v-stepper>
</template>
<script>
export default {
  name: 'stepper',
  props: {
    step: Number
  }
}
</script>
