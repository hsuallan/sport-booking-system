<template>
  <v-row align="center" justify="center">
    <v-col cols="8">
      <v-card class="mx-auto" color="" max-width="400">
        <v-card-title>
          <span class="title font-weight-light">以下是{{ this.$route.params.order.name }}先生/小姐的預約訊息</span>
        </v-card-title>
        <v-card-text class="headline font-weight-bold">
          <v-simple-table>
            <tbody>
              <tr>
                <td>位置</td>
                <td>日期</td>
                <td>時段</td>
              </tr>
              <tr>
                <td>{{ item.name }}</td>
                <td>{{ item.date }}</td>
                <td>{{ item.time }}</td>
              </tr>
            </tbody>
          </v-simple-table>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
export default {
  name: 'done',
  mounted: function () {
    this.$emit('step-change', 6)
    this.item = this.$route.params.item
  },
  data () {
    return {
      item: {}
    }
  }
}
</script>
