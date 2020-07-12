<template>
  <v-row align="center" justify="center">
    <v-col>
      <!-- <v-alert type="info"> Router value:{{ $route.params }} </v-alert> -->
      <v-card>
        <v-card-title>
          可預約時段
          <v-spacer></v-spacer>
          <v-text-field
            v-model="search"
            append-icon="mdi-magnify"
            label="Search"
            single-line
            hide-details
          ></v-text-field>
        </v-card-title>
        <v-data-table
          :loading="loading"
          :headers="headers"
          :items="status"
          :search="search"
          loading-text="Loading...."
        >
          <template v-slot:item.order="{ item }">
            <v-dialog
              v-model="dialog"
              max-width="500"
              v-if="item.order !== true"
              @click:outside="$emit('step-change', 3)"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  class="ma-2"
                  outlined
                  color="indigo"
                  v-bind="attrs"
                  v-on="on"
                  @click="$emit('step-change', 4)"
                  :disabled="item.order"
                >
                  我要預約
                </v-btn>
              </template>
              <v-card>
                <v-card-title class="headline">請填寫基本資料</v-card-title>
                <v-divider></v-divider>
                <v-card-subtitle>
                  <v-simple-table dense>
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
                </v-card-subtitle>
                <v-card-text>
                  <v-container>
                    <v-row no-gutters>
                      <v-col cols="5">
                        <v-text-field
                          label="預約人姓名*"
                          v-model="order.name"
                          required
                        ></v-text-field>
                      </v-col>
                      <v-col cols="1"> </v-col>
                      <v-col cols="6">
                        <v-text-field
                          label="預約人電話*"
                          v-model="order.phone"
                          required
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12">
                        <v-text-field
                          label="預約人電子郵件*"
                          v-model="order.mail"
                          required
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12">
                        <v-text-field
                          label="預約人身分證字號*"
                          v-model="order.id"
                          type="password"
                          required
                        ></v-text-field>
                      </v-col>
                    </v-row>
                    <v-row no-gutters>
                      <v-col cols="5">
                        <v-text-field
                          label="緊急聯絡人姓名"
                          v-model="order.emergencyName"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="1"> </v-col>
                      <v-col cols="6">
                        <v-text-field
                          label="緊急聯絡人電話"
                          v-model="order.emergencyPhone"
                        ></v-text-field>
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col cols="6">
                        <v-text-field
                          label="與緊急聯絡人之關係"
                          v-model="order.emergencyRelation"
                        ></v-text-field>
                      </v-col>
                    </v-row>
                  </v-container>
                  <small>*表示必須填寫</small>
                </v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn color="green darken-1" text @click="booking(item)"
                    >確定預約</v-btn
                  >
                  <v-btn
                    color="green darken-1"
                    text
                    @click="
                      dialog = false;
                      $emit('step-change', 3);
                    "
                    >再...讓我想一下<br />(機會4不等人的ㄛ)</v-btn
                  >
                </v-card-actions>
              </v-card>
            </v-dialog>
            <v-btn
              class="ma-2"
              outlined
              color="indigo"
              :disabled="item.order"
              v-else
              >我要預約</v-btn
            >
          </template>
        </v-data-table>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
export default {
  data () {
    return {
      search: '',
      loading: true,
      dialog: false,
      order: {},
      headers: [
        {
          text: '所在地區',
          align: 'start',
          value: 'location'
        },
        {
          text: '場地位置',
          sortable: false,
          value: 'name'
        },
        { text: '使用日期', value: 'date' },
        { text: '使用時段', value: 'time' },
        { text: '預約狀態', value: 'order' }
      ],
      status: [
        {
          location: '萬華區',
          name: '5F球場01',
          date: this.$route.params.date,
          time: '06:00 - 07:00',
          order: true
        },
        {
          location: '萬華區',
          name: '5F球場02',
          date: this.$route.params.date,
          time: '06:00 - 07:00',
          order: true

        },
        {
          location: '大安區',
          name: '3F球場03',
          date: this.$route.params.date,
          time: '07:00 - 08:00',
          order: false
        }
      ]
    }
  },
  methods: {
    booking: function (item) {
      /**
       * ajax here
       * post data this.order
       * put this.$router.replace in then() or final() to redirect to /done
       * set params.pw = query password
       */
      this.$router.replace({ name: 'done', params: { order: this.order, item: item, pw: '1a2f' } })
      console.table(this.order)
    }
  },
  mounted: function () {
    /**
     * ajax here
     * put this.loading = false in then() to close loading
     * post data this.$route.params
     * let status = ajax_result
     */
    this.loading = false
  }
}
</script>
