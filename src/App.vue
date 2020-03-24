<template>
  <v-app>
    <navigation-drawer></navigation-drawer>
    <v-content>
      <images-view />
    </v-content>
    <v-footer color="indigo" app>
      <span class="white--text">Gerard Llanas &copy; 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
import NavigationDrawer from "./components/NavigationDrawer";
import ImagesView from "./views/ImagesView";
export default {
  props: {
    source: String
  },
  components: {
    NavigationDrawer,
    ImagesView
  }
};
</script>