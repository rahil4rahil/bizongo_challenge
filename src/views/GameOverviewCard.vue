<template>
    <v-card class="card-background">
        <v-card-title primary-title>
            <v-layout row wrap>
                <v-flex xs12 sm6 md6 class="text-xs-left text-md-left">
                    <span class="title">{{ gameData.Name }}</span>
                </v-flex>
                <v-flex xs12 sm6 md6 class="text-xs-left text-sm-right text-md-right">
                    <span class="subheading mr-2">Rank:</span><span class="title">#{{ gameData.Rank }}</span>
                </v-flex>
            </v-layout>
        </v-card-title>
        <v-card-text class="mt-0 pt-0">
            <v-layout row wrap>
                <v-flex xs12 sm6 md4 class="text-xs-left text-md-left">
                    <span class="body-2 font-weight-light">Platform: </span><span class="body-2">{{ gameData.Platform }}</span>
                </v-flex>
                <v-flex xs12 sm6 md4 class="text-xs-left text-sm-right text-md-center ">
                    <span class="body-2 font-weight-light">Year: </span><span class="body-2">{{ gameData.Year }}</span>
                </v-flex>
                <v-flex xs12 sm6 md4 class="text-xs-left text-sm-left text-md-right">
                    <span class="body-2 font-weight-light">Publisher: </span><span class="body-2">{{ gameData.Publisher }}</span>
                </v-flex>
                <v-flex xs12 sm6 md4 class="text-xs-left text-sm-right text-md-left">
                    <span class="body-2 font-weight-light">Genre: </span><span class="body-2">{{ gameData.Genre }}</span>
                </v-flex>
                <v-flex xs12 sm6 md4 class="text-xs-left text-md-center">
                    <span class="body-2 font-weight-light">Global Sales: </span><span class="body-2">{{ gameData.Global_Sales }}</span>
                </v-flex>
            </v-layout>
        </v-card-text>
    </v-card>
</template>

<script>
export default {
    name: "GameOverviewCard",
    data: () => {
        return {

        }
    },
    props: {
        gameData: {
            type: Object,
            default: null
        }
    }
}
</script>

<style>
.card-background {
    background-color: rgba(0, 0, 0, 0.3) !important;
    border-radius: 10px !important;
    cursor: pointer;
    transition: all .5s;
}

.card-background:hover {
    box-shadow: 0 5px 20px black;
}

</style>
