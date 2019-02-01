<template>
  <v-flex d-flex xs12 sm12 md8>
    <v-card flat class="scroll-y" height="680">
      <v-container>
        <v-layout align-center justify-center row fill-height>
          <v-progress-circular
            v-if="loader"
            :size="100"
            color="lime darken-2"
            indeterminate
          >{{message}}</v-progress-circular>
        </v-layout>
        <v-timeline class="pa-0">
          <v-timeline-item v-for="(data,n) in sort" :key="n" large>
            <v-avatar slot="icon">
              <img :src="avatar" class="avatar">
            </v-avatar>
            <span
              slot="opposite"
              class="head font-weight-light lime--text text--darken-3"
            >{{moment(data.pushed_at)}}</span>
            <v-card class="lime darken-3" tile>
              <v-card-title
                style="height:50px"
                class="head blue-grey darken-4 amber--text text--lighten-2"
              >{{removeDash(data.name)}}</v-card-title>
              <v-card-text class="py-0 white--text">
                <v-btn :href="data.html_url" absolute bottom right fab color="blue-grey darken-4">
                  <v-icon color="white">send</v-icon>
                </v-btn>
                <v-timeline align-top dense>
                  <v-timeline-item color="blue-grey darken-4" small>
                    <v-layout pt-3>
                      <v-flex xs3>
                        <strong>ID</strong>
                        <div class="caption">{{data.id}}</div>
                      </v-flex>
                    </v-layout>
                  </v-timeline-item>
                  <v-timeline-item color="blue-grey darken-4" small>
                    <v-layout pt-3>
                      <v-flex xs3>
                        <strong>Name</strong>
                        <div class="caption">{{data.name}}</div>
                      </v-flex>
                    </v-layout>
                  </v-timeline-item>
                  <v-timeline-item color="blue-grey darken-4" small>
                    <v-layout pt-3>
                      <v-flex xs3>
                        <strong>Language</strong>
                        <div class="caption mb-2">{{data.language}}</div>
                      </v-flex>
                      <v-flex class="mx-4">
                        <v-avatar color="blue-grey darken-4">
                          <img class="icon" :src="icons(data.language)">
                        </v-avatar>
                      </v-flex>
                    </v-layout>
                  </v-timeline-item>
                </v-timeline>
              </v-card-text>
            </v-card>
          </v-timeline-item>
        </v-timeline>
      </v-container>
    </v-card>
  </v-flex>
</template>

<script>
import moment from "moment";
import axios from "axios";
import html from "@/assets/html-5.png";
import js from "@/assets/js.png";
import vue from "@/assets/vue.png";

export default {
  props: ["avatar"],
  data() {
    return {
      desc: "This is Projects Page",
      datas: [],
      html,
      js,
      vue,
      loader: true,
      message: "Fetching from GitHub"
    };
  },
  computed: {
    sort() {
      return this.datas
        .slice()
        .sort((a, b) => (a.pushed_at > b.pushed_at ? 1 : 1));
    }
  },

  methods: {
    removeDash(args) {
      if (args) {
        let replace = args.replace(/[-_]/g, " ");
        let result = replace.toUpperCase();
        return result;
      }
    },
    icons(lang) {
      if (lang) {
        let lowercase = lang.toLowerCase();
        if (lowercase === "html") return html;
        if (lowercase === "javascript") return js;
        if (lowercase === "vue") return vue;
      }
    },
    moment(date) {
      if (date) {
        return moment(date)
          .format("dddd, MMM Do YYYY")
          .toUpperCase();
      }
    }
  },

  mounted() {
    axios("https://api.github.com/users/joeprabawa/repos").then(({ data }) => {
      this.datas = data;
      this.loader = false;
    });
  }
};
</script>

<style scoped>
.avatar {
  object-fit: cover;
}

.icons,
.icon {
  object-fit: cover;
}

.v-card__title.head,
span.head {
  letter-spacing: 0.4rem !important;
}
</style>
