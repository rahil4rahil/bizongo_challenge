<template>
  <v-app app>
    <v-content class="container-wrapper">
        <v-container>
          <v-layout row wrap>
            <v-flex xs12>
              <router-view/>
            </v-flex>
          </v-layout>
        </v-container>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data () {
    return {
      //
    } 
  }
}
</script>

<style>
* {
  padding:0;
  margin:0;
  box-sizing: inherit;
}

html {
  font-size: 62.5%  
}

body {
  box-sizing: border-box;
}
p, span {
  color: #fff;
}

.container-wrapper {
  background-image: linear-gradient(to right bottom, rgba(126, 213, 111, 0.801), rgba(40, 180, 133, 0.801)), url('./assets/background.jpg');
  background-position: top;
  background-size:cover;
  background-repeat:repeat;
}
</style>

