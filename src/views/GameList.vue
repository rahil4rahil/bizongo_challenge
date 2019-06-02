<template>
  <v-layout row wrap>
    <v-flex xs12>
      <GameListHeader/>
    </v-flex>
    <v-flex xs12>
      <v-layout row wrap>
        <v-flex xs12 class="mb-2" v-for="item in gameList" :key="item.Rank" @click="openDetailPage(item)">
          <template >
            <GameOverviewCard :gameData="item"/>
          </template>
        </v-flex>
      </v-layout>
    </v-flex>
    <v-flex xs12>
      <GameListFooter  :fitleredList="filteredList" :currentWindow="showWindow" @next="showNextData" @prev="showPrevData"/>
    </v-flex>
  </v-layout>
</template>
<script>
import GameOverviewCard from '@/views/GameOverviewCard'
import GameListFooter from '@/views/GameListFooter'
import GameListHeader from '@/views/GameListHeader'

export default {
  data: () => {
    return {
      showWindow:0,
      gameList: [],
    }
  },
  props: {
    filteredList: {
      type: Array,
      default: []
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
  components: {
    GameOverviewCard,
    GameListFooter,
    GameListHeader
  },
  watch: {
    filteredList() {
      this.gameList = JSON.parse(JSON.stringify(this.filteredList)).splice(this.showWindow, 10);
    }
  },
  mounted() {
    console.log(this.filteredList)
    this.gameList = JSON.parse(JSON.stringify(this.filteredList)).splice(this.showWindow, 10);
  },
  methods: {
    openDetailPage(item) {
      this.selectedItem = item
      this.$router.push({ path: '/gameDetail/' + item.Rank })
    },
    showNextData() {
      this.showWindow += 10
      this.gameList = JSON.parse(JSON.stringify(this.filteredList)).splice(this.showWindow, 10);
    },
    showPrevData() {
      this.showWindow -= 10
      this.gameList = JSON.parse(JSON.stringify(this.filteredList)).splice(this.showWindow, 10);
    }
  }
}
</script>
