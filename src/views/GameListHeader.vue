<template>
    <v-layout row wrap>
        <v-flex xs4 class="text-xs-right pb-2">
            <v-select
                v-model="selectedOption"
                dark
                label="Sort By"
                :items="sortList"
                color="white"
                clearable
            >
            </v-select>
        </v-flex>
    </v-layout>
</template>

<script>
export default {
    name: 'GameListHeader',
    data: () => {
        return {
            sortList: ['Year']
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

    }
}
</script>

<style>
.v-list__tile__title {
    color: black
}
</style>
