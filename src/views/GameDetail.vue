<template>
    <v-layout row wrap justify-center class="elevation-2 pa-3 list-container" v-if="selectedItem">
    <v-flex>
      <v-btn
      color="error"
      class="text-capitalize"
      @click="back"
      >
        Back
      </v-btn>
    </v-flex>
    <v-flex xs12 md12 class="text-xs-center">
      <span class="display-1">{{ selectedItem.Name}}</span>
    </v-flex>
    <v-flex xs12 md8 class="text-xs-left text-md-right pl-5">
      <v-layout row wrap>
        <v-flex xs12 pt-4 sm6 md4 class="text-xs-left text-md-left">
            <span class="body-2 font-weight-light">Platform: </span><span class="body-2">{{ selectedItem.Platform }}</span>
        </v-flex>
        <v-flex xs12 pt-4 sm6 md4 class="text-xs-left text-sm-left text-md-left ">
            <span class="body-2 font-weight-light">Year: </span><span class="body-2">{{ selectedItem.Year }}</span>
        </v-flex>
        <v-flex xs12 pt-4 sm6 md4 class="text-xs-left text-sm-left text-md-left">
            <span class="body-2 font-weight-light">Publisher: </span><span class="body-2">{{ selectedItem.Publisher }}</span>
        </v-flex>
        <v-flex xs12 pt-4 sm6 md4 class="text-xs-left text-sm-left text-md-left">
            <span class="body-2 font-weight-light">Genre: </span><span class="body-2">{{ selectedItem.Genre }}</span>
        </v-flex>
        <v-flex xs12 pt-4 sm6 md4 class="text-xs-left text-md-left">
            <span class="body-2 font-weight-light">Global Sales: </span><span class="body-2">{{ selectedItem.Global_Sales }}</span>
        </v-flex>
        <v-flex xs12 pt-4 sm6 md4 class="text-xs-left text-md-left">
            <span class="body-2 font-weight-light">Rank: </span><span class="body-2">{{ selectedItem.Rank }}</span>
        </v-flex>
    </v-layout>
    </v-flex>
    <v-flex xs12 md4 class="text-xs-center text-md-right pr-5 pt-3">
       <v-progress-circular
        :rotate="270"
        :size="100"
        :width="15"
        :value="selectedItem.Global_Sales"
        color="white"
      >
        {{ selectedItem.Global_Sales }}
      </v-progress-circular>
    </v-flex>
    
  </v-layout>
</template>

<script>
import gameData from '@/data/games.json'
export default {  
  name: 'GameDetail',
  data: () => {
    return {
    }
  },
  computed: {
    selectedItem: {
      set(val) {
        this.$store.state.selectedItem = val
      },
      get() {
        return this.$store.state.selectedItem
      }
    }
  },
  methods: {
    back() {
      this.$router.push({path: '/'})
    }
  },
  mounted() {
    let vm = this
    if (!this.selectedItem) {
      this.selectedItem = gameData.find((element) => {
        return element.Rank == vm.$route.params.id
      })
    }
  }
}
</script>

<style>

</style>
