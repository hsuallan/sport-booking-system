<template>
  <div class="home">
    <v-row class="text-center mt-2">
      <v-img
        :src="require('../assets/Badminton1.png')"
        class="my-3 Badminton"
        contain
        :max-height="width > 600 ? 200 : 100"
        @click="$router.push({ path: '/badminton' });$emit('step-change',2)"
      >
      </v-img>
      <v-img
        :src="require('../assets/Basketball1.png')"
        class="my-3 Basketball"
        contain
        :max-height="width > 600 ? 200 : 100"
        @click="$router.push({ path: '/basketball' });$emit('step-change',2)"
      >
      </v-img>
    </v-row>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {

  },
  mounted () {
    window.addEventListener('resize', () => {
      this.width = window.screen.width
    })
  },
  data () {
    return {
      width: window.screen.width
    }
  }
}
</script>
<style scoped>
.Basketball:hover {
  transform: scale(1.2) rotate(140deg);
  transition: cubic-bezier(0.68, -0.55, 0.265, 1.55);
  transition-duration: 1s;
  cursor: pointer;
}
.Badminton:hover {
  transform: scale(1.2) rotate(140deg);
  transition: cubic-bezier(0.68, -0.55, 0.265, 1.55);
  transition-duration: 1s;
  cursor: pointer;
}
</style>
