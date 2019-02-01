<template>
  <v-app>
    <v-content>
      <v-container fluid grid-list-md fill-height>
        <v-layout row wrap align-space-around>
          <component :is="render" :me="me" :avatar="Avatar" :size="avatarSize"></component>

          <v-flex d-flex xs12 sm6 md4>
            <v-layout row wrap>
              <v-flex d-flex>
                <v-card color="blue-grey darken-4" class="pa-2" dark tile>
                  <v-layout align-center justify-center fill-height>
                    <v-btn @click="change" outline color="teal lighten-2">
                      <v-icon left>{{buttonState? 'home': 'perm_identity'}}</v-icon>
                      {{buttonState ? 'Home' : 'About'}}
                    </v-btn>
                  </v-layout>
                </v-card>
              </v-flex>
              <v-flex d-flex>
                <v-layout row>
                  <v-flex v-for="(n, i) in buttons" :key="i" d-flex xs12>
                    <v-card :color="n.bg_color" class="pa-2" dark tile>
                      <v-layout align-center justify-center fill-height>
                        <v-btn outline :color="n.color" @click="render=n.title">
                          <v-icon dark left>{{n.icon}}</v-icon>
                          {{n.title}}
                        </v-btn>
                      </v-layout>
                    </v-card>
                  </v-flex>
                </v-layout>
              </v-flex>
              <v-flex d-flex>
                <v-card color="blue-grey darken-4" class="pa-2" dark tile>
                  <v-layout align-center justify-center fill-height>
                    <v-btn outline color="amber" @click="render='Links'">
                      <v-icon dark left>link</v-icon>links
                    </v-btn>
                  </v-layout>
                </v-card>
              </v-flex>
            </v-layout>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Avatar from "@/assets/avatar.jpeg";
import Home from "@/components/Home";
import About from "@/components/About";
import Projects from "@/components/Projects";
import Links from "@/components/Links";
import Skills from "@/components/Skills";

export default {
  name: "App",
  data: () => {
    return {
      buttonState: false,
      render: "Home",
      me: {
        nama: "Indra Prabawa",
        sub: "Web Developer"
      },
      Avatar,
      avatarSize: "225px",
      buttons: [
        {
          title: "Skills",
          bg_color: "white",
          color: "pink darken-3",
          icon: "category"
        },
        {
          title: "Projects",
          bg_color: "white",
          color: "lime darken-3",
          icon: "waves"
        }
      ]
    };
  },
  methods: {
    change() {
      this.buttonState ? (this.render = "Home") : (this.render = "About");
      return (this.buttonState = !this.buttonState);
    }
  },
  components: {
    Home,
    Links,
    Skills,
    Projects,
    About
  }
};
</script>

<style >
.avatar {
  object-fit: cover;
}

.v-card__text.sub {
  margin-top: -2rem;
}
</style>

