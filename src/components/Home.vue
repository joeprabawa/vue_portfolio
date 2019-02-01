<template>
  <v-flex d-flex xs12 sm6 md8>
    <v-card color="white" flat tile class="text-xs-center">
      <v-layout align-center justify-center column fill-height>
        <v-avatar :size="size" color="yellow lighten-2 my-4">
          <img :src="avatar" alt="avatar" class="avatar mt-5">
        </v-avatar>
        <v-card-title dark class="title mt-5 black--text">{{me.nama}}</v-card-title>
        <v-card-text class="text-xs-center sub grey--text text--lighten-1">{{ me.sub }}</v-card-text>
      </v-layout>
    </v-card>
  </v-flex>
</template>

<script>
export default {
  name: "Home",
  props: ["me", "avatar", "size"],
  data() {
    return {};
  }
};
</script>

<style scoped>
</style>
