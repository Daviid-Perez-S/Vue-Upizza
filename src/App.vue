<template>
  <v-app>
    <v-toolbar app color="amber">
      <v-toolbar-title class="headline">
        <span><a href="/" id="main-title">UPizza</a></span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar>

    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'
export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
  #main-title {
    text-decoration: none;
    color: black;
  }
</style>

