<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-icon size="40">
          mdi-rocket-launch
        </v-icon>
        <div class="text-lg-h6"> RocketBook</div>
      </div>

      <v-spacer></v-spacer>

      <v-btn href="" target="_blank" text>
        <span class="mr-2">btn</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <Booking />
    </v-main>
  </v-app>
</template>

<script>
import Booking from './components/Booking.vue';


export default {
  name: 'App',

  components: {
    Booking
  },

  data: () => ({
    //
  }),
};
</script>
