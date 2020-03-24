<template>
  <v-card>
    <v-img
      v-bind:src="src"
      class="white--text align-end"
      gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
      height="200px"
    >
      <v-card-title>{{title}}</v-card-title>
    </v-img>
  </v-card>
</template>

<script>
export default {
  name: "ImageCard",
  props: ["src", "title"],
  data: () => ({}),
  mounted() {}
};
</script>
