<template>
  <v-flex d-flex xs12 sm6 md8>
    <v-card color="white" dark tile flat pa-0>
      <v-container grid-list-md text-xs-center fill-height>
        <v-layout column justify-center align-center>
          <v-flex d-flex>
            <v-layout row wrap>
              <v-flex d-flex xs12 md4 v-for="(skill,i) in skills" :key="i">
                <v-card width="260" dark tile color="blue-grey darken-4" class="pa-3">
                  <v-layout fill-height justify-center align-center>
                    <v-progress-circular
                      :rotate="skill.rotate"
                      :size="160"
                      :width="40"
                      :max="skill.max"
                      :value="skill.value"
                      :color="skill.color"
                    >
                      <v-card-title title>{{skill.name}}</v-card-title>
                    </v-progress-circular>
                  </v-layout>
                  <div class="info font-weight-bold display-1">{{skill.value}}</div>
                </v-card>
              </v-flex>
            </v-layout>
          </v-flex>

          <v-flex d-flex>
            <v-layout row wrap>
              <v-flex d-flex xs12 sm6 md3 v-for="(skill,i) in skillstwo" :key="i">
                <v-card width="260" dark tile color="blue-grey darken-4" class="pa-3 my-2">
                  <v-layout align-center justify-center fill-height>
                    <v-progress-circular
                      :rotate="skill.rotate"
                      :size="160"
                      :width="40"
                      :max="skill.max"
                      :value="skill.value"
                      :color="skill.color"
                    >
                      <v-card-title title>{{skill.name}}</v-card-title>
                    </v-progress-circular>
                  </v-layout>
                  <div class="info font-weight-bold display-1">{{skill.value}}</div>
                </v-card>
              </v-flex>
              <v-flex d-flex xs12 sm6 md6>
                <v-card width="260" dark tile color="blue-grey darken-4" class="pa-3 my-2">
                  <v-layout align-center justify-center fill-height>
                    <v-progress-circular
                      :rotate="skill.rotate"
                      :size="160"
                      :width="40"
                      :max="skill.max"
                      :value="skill.value"
                      :color="skill.color"
                    >
                      <v-card-title title>{{skill.name}}</v-card-title>
                    </v-progress-circular>
                  </v-layout>
                  <div class="info font-weight-bold display-1">{{skill.value}}</div>
                </v-card>
              </v-flex>
            </v-layout>
          </v-flex>
        </v-layout>
      </v-container>
    </v-card>
  </v-flex>
</template>

<script>
export default {
  data() {
    return {
      interval: {},
      skill: {
        name: "Vue JS",
        rotate: -180,
        value: 0,
        max: 90,
        color: "light green-2"
      },

      skills: [
        {
          name: "HTML",
          rotate: 360,
          value: 0,
          max: 80,
          color: "pink darken-1"
        },
        {
          name: "CSS",
          rotate: 180,
          value: 0,
          max: 70,
          color: "cyan darken-3"
        },
        {
          name: "Javascript",
          rotate: -90,
          value: 0,
          max: 70,
          color: "lime darken-2"
        }
      ],
      skillstwo: [
        {
          name: "Node JS",
          rotate: 90,
          value: 0,
          max: 70,
          color: "green lighten-1"
        },
        {
          name: "Express",
          rotate: 360,
          value: 0,
          max: 70,
          color: "lime darken-2"
        }

        // {
        //   name: "Firebase",
        //   rotate: -180,
        //   value: 0,
        //   max: 70,
        //   color: "amber lighten-2"
        // }
      ]
    };
  },

  mounted() {
    this.interval = setInterval(() => {
      if (this.skill.value === this.skill.max) {
        return this.skill.value === this.skill.max;
      }

      this.skill.value += this.skill.max;

      this.skills.forEach(skill => {
        if (skill.value === skill.max) {
          return (skill.value = skill.max);
        }
        skill.value += skill.max;
      });
      this.skillstwo.forEach(skill => {
        if (skill.value === skill.max) {
          return (skill.value = skill.max);
        }
        skill.value += skill.max;
      });
    }, 200);
  }
};
</script>

<style scoped>
.v-card .info {
  position: absolute;
  bottom: 0.3rem;
  right: 1rem;
  color: #cac9c9;
}

.info {
  background-color: transparent !important;
}
</style>
