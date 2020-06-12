<template>
  <div class="Query">
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="4">
        <v-card class="elevation-12">
          <v-toolbar color="primary" dark flat>
            <v-toolbar-title>查詢您的預約</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <v-form>
              <v-text-field
                label="身份證字號"
                name="login"
                prepend-icon="mdi-account"
                v-model="id"
                type="text"
                counter="10"
                required
              ></v-text-field>

              <v-text-field
                id="password"
                label="查詢金鑰"
                name="password"
                prepend-icon="mdi-lock"
                type="password"
                v-model="pw"
                counter="4"
                required
              ></v-text-field>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="primary" @click="query('')">查詢</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <v-row align="center" justify="center" v-if="queryData.length !== 0">
      <v-col cols="12" sm="8" md="4">
        <v-carousel height="350" hide-delimiter-background show-arrows-on-hover>
          <v-carousel-item v-for="(item, i) in queryData" :key="i">
            <v-sheet :color="item.color" height="100%">
              <v-row class="fill-height" align="center" justify="center">
                <div class="display-3">{{ item.text }} Slide</div>
              </v-row>
            </v-sheet>
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>
  </div>
</template>
<script>
// @ is an alias to /src

export default {
  name: 'Query',
  components: {
  },
  methods: {
    colorgen: () => {
      return '#' + ((1 << 24) * Math.random() | 0).toString(16)
    },
    query: () => {
      // TODO:ajax
    }
  },
  data () {
    return {
      id: '',
      pw: '',
      queryData: [
        {
          text: 'first',
          color: this.colorgen()
        },
        {
          text: 'Second',
          color: this.colorgen()
        },
        {
          text: 'Third',
          color: this.colorgen()
        }
      ]
    }
  }
}
</script>
