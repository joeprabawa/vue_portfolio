<template>
  <v-flex d-flex xs12 sm6 md8>
    <v-card color="white" dark tile flat>
      <v-layout align-center justify-center row fill-height>
        <v-container>
          <v-card-title dark class="mt-5 black--text pa-5">
            <p class="text">
              started off back in 2012, i took medical background, called
              <i>medical records</i> major in my former university. And yes, i failed in the middle of the progress. No reason needed to explain why i failed there, afterwards on late 2016 i took an interest in web development. The reason why i put interest in web development was when i became a trainee at Bali State Hospital, i felt during the trainee program the presence of technology for
              <i>medical records</i> could be useful for rapid communiacation between patient and the healtcare practitioners. So i began my journey to learn web development after that, and currently i took computer major on STIKI Indonesia.
            </p>
          </v-card-title>
        </v-container>
      </v-layout>
    </v-card>
  </v-flex>
</template>

<script>
export default {
  data() {
    return {};
  }
};
</script>

<style scoped>
p:first-child:first-letter {
  color: #26a69a;
  float: left;
  font-family: Georgia;
  margin: 0 10px 3rem 0;
  font-size: 10rem;
  line-height: 0.2rem;
  padding: 1rem 5px;
  /* background-color: #263238; */
}

p {
  text-align: justify;
  line-height: 2rem;
}
</style>
