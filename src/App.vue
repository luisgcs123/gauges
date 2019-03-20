<template>
<v-app>
  <!-- <v-navigation-drawer app></v-navigation-drawer>
  <v-toolbar app></v-toolbar> -->
  <v-content transition="slide-x-transition">
    <v-container fluid>
      <router-view></router-view>
    </v-container>
  </v-content>
</v-app>
</template>

<style>
   #app {
    background-color: #3a8dde;
  }
   html{
      overflow-y: hidden;
    }
</style>
