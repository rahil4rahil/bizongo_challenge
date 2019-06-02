<template>
    <v-layout row wrap justify-center>
        <v-flex md6 lg6 xs10 sm8>
             <v-autocomplete
                v-model="selectedGame"
                :items="data"
                :search-input.sync="fitlerGameList"
                class="auto-complete-wrapper"
                flat
                item-text="Name"
                item-value="Rank"
                hide-no-data
                hide-details
                no-data-text
                label="Search Game"
                return-object
                clearable
                @click:clear="resetList"
                @change="seachItemChanged($event)"
                solo-inverted
            ></v-autocomplete>
        </v-flex>
    </v-layout>
</template>

<script>
import nameList from '@/data/games.json'
export default {    
    name: 'SearchGameAuto',
    data: () => {
        return {
            selectedGame: null,
            data: [],
            fitlerGameList:[]
        }
    },
    watch: {
        fitlerGameList(val) {
            if (!val) {
                this.$emit('filteredList', this.data)                
            }
            val && val !== this.selectedGame 
            // && this.querySelections(val)
        },
    },
    mounted() {
        this.data = nameList
    },
    methods: {
        seachItemChanged(item) {
            this.$emit('searchItemChanged', item)
            let filterList = []
            filterList.push(item)
            this.$emit('filteredList', filterList)
        },
        resetList() {
            this.$emit('filteredList', this.data)
        },
        querySelections(val) {
            new Promise((resolve, reject) => {
                let filterList = this.data.filter((element) => {
                    if (typeof element.Name == 'string' && element.Name.toLowerCase().indexOf(val) > -1) {
                        return element
                    }
                })
                resolve(filterList)
            }).then((result) => {
                this.$emit('filteredList', result)
            })
        },
    }

}
</script>

<style>
.auto-complete-wrapper {
    /* max-width: 400px; */
}
</style>
