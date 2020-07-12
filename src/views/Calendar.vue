<template>
  <v-row align="center" justify="center" class="ml-2 mr-2">
    <v-col>
      <!-- <v-alert type="info"> Router value:{{ $route.params }} </v-alert> -->
      <v-sheet height="500" class="mr-4">
        <v-btn class="ma-2" @click="$refs.calendar.prev()">
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
        <v-btn class="ma-2" @click="$refs.calendar.next()">
          <v-icon>mdi-chevron-right</v-icon>
        </v-btn>
        <v-calendar
          ref="calendar"
          :events="events"
          color="primary"
          type="month"
          v-model="clickDate"
        ></v-calendar>
      </v-sheet>
    </v-col>
  </v-row>
</template>
<script>
export default {
  name: 'Calendar',
  components: {
  },
  data () {
    return {
      clickDate: '',
      events: [
        {
          name: '可以預約',
          start: ''
        },
        {
          name: '可以預約',
          start: ''
        },
        {
          name: '可以預約',
          start: ''
        },
        {
          name: '可以預約',
          start: ''
        },
        {
          name: '可以預約',
          start: ''
        },
        {
          name: '可以預約',
          start: ''
        },
        {
          name: '可以預約',
          start: ''
        }
      ]
    }
  },
  watch: {
    clickDate: function (date) {
      // ajax NOT here => date.vue mounted function
      if (this.events.filter((x) => { return x.start === date }).length === 1) {
        this.$emit('step-change', 3)
        this.$router.push({ path: `/${this.$route.params.sport}/${date}` })
      }
    }
  },
  created () {
    // gendate for demo
    const today = new Date()
    const year = today.getFullYear()
    const date = today.getDate()
    const month = today.getMonth()
    const monthStr = month < 10 ? '0' + (month + 1).toString() : (month + 1).toString()
    this.events.forEach((element, i) => {
      element.start = `${year}-${monthStr}-${date + 1 + i}`
    })
  }
}
</script>
