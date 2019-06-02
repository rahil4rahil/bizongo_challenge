<template>
    <v-layout row wrap>
        <v-flex xs12>
            <SearchGameAuto @filteredList="setFilteredList"/>
        </v-flex>
        <v-flex xs12>
            <v-container>
                <v-layout row wrap  class="elevation-2 pa-3 list-container">
                    <v-flex xs12>
                        <GameList :filteredList="filteredList"/>
                    </v-flex>
                </v-layout>
            </v-container>
        </v-flex>
    </v-layout>
</template>

<script>
import SearchGameAuto from '@/components/SearchGameAuto'
import GameList from '@/views/GameList'
import gameList from '@/data/games.json'

export default {
    name:'Home',
    data: () => {
        return {
            filteredList: []
        }
    },
    mounted() {
        if (this.selectedOption) {
            this.filteredList = JSON.parse(JSON.stringify(gameList)).sort((a, b) => {
                return b.Year - a.Year;
            });
        }
        else {
            this.filteredList = gameList
        }
    },
    components: {
        SearchGameAuto,
        GameList,
    },
    watch: {
        selectedOption() {
            if (this.selectedOption) {
                this.filteredList = JSON.parse(JSON.stringify(gameList)).sort((a, b) => {
                    return b.Year - a.Year;
                });
            }
            else {
                this.filteredList = gameList
            }
        }
    },
    computed: {
        selectedOption: {
            set(val) {
                this.$store.state.selectedOption = val
            },
            get() {
                return this.$store.state.selectedOption
            }
        }
    },
    methods: {
        setFilteredList(val) {
            this.filteredList = val
        }
    }
}
</script>

<style>
    .list-container {
        background: rgba(0, 0, 0, .5);
        border-radius: 20px;
    }
</style>
