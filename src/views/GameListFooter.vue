<template>
    <v-layout row wrap>
        <v-flex xs6 class="text-xs-left">    
            <v-icon>fa-arrow-alt-left</v-icon>
            <v-btn class="ma-0 mt-1" :disabled="currentWindow == 0" @click="pageChanged(-1)" color="primary">Prev</v-btn>
        </v-flex>
        <v-flex xs6 class="text-xs-right">
            <v-btn class="ma-0 mt-1" color="primary" :disabled="currentWindow + 10 >= fitleredList.length" @click="pageChanged(1)">Next</v-btn>
        </v-flex>
    </v-layout>
</template>

<script>
export default {
    name:'GameListFooter',
    data: () => {
        return {
            gameData:[]
        }
    },
    mounted() {
    },
    props: {
        currentWindow: {
            type: Number,
            default:0
        },
        fitleredList: {
            type: Array,
            default: []
        }
    },
    methods: {
        pageChanged(step) {
            if (step == 1) {
                this.$emit('next')
            }
            else if (step == -1) {
                this.$emit('prev')
            }
        },
    }
}
</script>

<style>

</style>
