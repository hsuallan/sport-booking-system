<template>
  <v-row align="center" justify="center">
    <v-col>
      <v-card class="mx-auto" color="" max-width="500">
        <v-card-title>
          <span class="title font-weight-light">以下是{{ this.$route.params.order.name }}先生/小姐的預約訊息</span>
        </v-card-title>
        <v-card-subtitle>
            <span class="title font-weight-light">查詢密碼為: <em>{{ this.$route.params.pw }}</em></span>
        </v-card-subtitle>
        <v-card-text class="headline font-weight-bold">
          <v-simple-table>
            <tbody>
              <tr>
                <td>地區</td>
                <td>位置</td>
                <td>日期</td>
                <td>時段</td>
              </tr>
              <tr>
                <td>{{ item.location }}</td>
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
