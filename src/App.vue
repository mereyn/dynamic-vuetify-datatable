<template>
  <v-app>
    <v-content>
      <v-btn color="success" @click="selectedComponent = 'HomePage'">Home</v-btn>
      <v-btn color="info" @click="selectedComponent = 'AboutUsPage'">About Us</v-btn>
      <hr>
      <v-container fluid>
        <keep-alive>
          <component :is="selectedComponent"></component>
        </keep-alive>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import AboutUs from "./components/AboutUs";
import Home from "./components/Home";

export default {
  data: function() {
    return {
      selectedComponent: "HomePage"
    };
  },
  name: "App",
  components: {
    AboutUsPage: AboutUs,
    HomePage: Home
  }
};
</script>
