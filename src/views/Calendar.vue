<template>
  <v-row align="center" justify="center">
    <v-col cols="8">
      <v-alert type="info"> Router value:{{ $route.params }} </v-alert>
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
          start: '2020-06-19'
        },
        {
          name: '可以預約',
          start: '2020-06-20'
        },
        {
          name: '可以預約',
          start: '2020-06-21'
        },
        {
          name: '可以預約',
          start: '2020-06-22'
        },
        {
          name: '可以預約',
          start: '2020-06-23'
        },
        {
          name: '可以預約',
          start: '2020-06-24'
        },
        {
          name: '可以預約',
          start: '2020-06-25'
        }
      ]
    }
  },
  watch: {
    clickDate: function (date) {
      // ajax
      if (this.events.filter((x) => { return x.start === date }).length === 1) {
        // 可以預約的日子
        this.$router.push({ path: `/${this.$route.params.sport}/${date}` })
      }
    }
  }
}
</script>
