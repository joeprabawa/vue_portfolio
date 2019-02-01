<template>
  <v-flex d-flex xs12 sm6 md8>
    <v-card color="white" tile flat class="text-xs-center">
      <v-container fluid fill-height>
        <v-flex>
          <v-layout align-center justify-center row wrap fill-height>
            <v-flex xs12 sm6 md6>
              <v-card-title
                color="light-grey text-xs-center"
                class="display-2 font-weight-light"
              >Lets Connected!</v-card-title>
              <v-form v-model="valid">
                <v-layout row>
                  <v-flex>
                    <v-text-field
                      :rules="emailRules"
                      v-model="data.email"
                      label="Email"
                      append-icon="email"
                      outline
                    ></v-text-field>
                  </v-flex>
                </v-layout>
                <v-layout row>
                  <v-flex>
                    <v-text-field
                      :rules="nameRules"
                      v-model="data.name"
                      label="Name"
                      append-icon="perm_identity"
                      outline
                    ></v-text-field>
                  </v-flex>
                </v-layout>
                <v-layout row>
                  <v-flex>
                    <v-btn
                      block
                      large
                      @click="submit"
                      flat
                      outline
                      :disabled="!valid"
                      color="success"
                    >Submit</v-btn>
                  </v-flex>
                </v-layout>
              </v-form>
              <v-layout row>
                <v-flex>
                  <v-card color="blue grey darken-4" class="text-xs-center" dark>
                    <v-card-text>Made with
                      <v-avatar class="ml-2" :tile="true" :size="size">
                        <img :src="logo">
                      </v-avatar>
                      <v-avatar :tile="true" :size="size">
                        <img :src="now">
                      </v-avatar>
                      <v-avatar class="mx-1" :tile="true" :size="fsSize">
                        <img :src="fs">
                      </v-avatar>
                    </v-card-text>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </v-flex>
      </v-container>
    </v-card>
  </v-flex>
</template>

<script>
import logo from "@/assets/logo.png";
import now from "@/assets/now-white.svg";
import fs from "@/assets/firestore.svg";
export default {
  name: "Links",
  data() {
    return {
      size: 25,
      fsSize: 30,
      logo,
      now,
      fs,
      links: ["Home", "About Us", "Team", "Services", "Blog", "Contact Us"],
      valid: false,
      data: {
        name: "",
        email: ""
      },
      nameRules: [
        v => !!v || "Name is required",
        v => v.length <= 20 || `Name must be less than ${v.length} characters`
      ],
      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+/.test(v) || "E-mail must be valid"
      ]
    };
  },
  methods: {
    submit() {}
  }
};
</script>

<style>
</style>
