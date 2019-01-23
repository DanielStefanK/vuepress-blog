<template>
  <v-app light>
    <v-toolbar color="purple darken-4">
      <v-toolbar-items>
        <v-btn class="white--text" color="purple darken-3" to="/">Home</v-btn>
        <v-btn class="white--text" color="purple darken-3" to="/aboutme.html">About Me</v-btn>
        <v-btn class="white--text" color="purple darken-3" to="/feed.html">Blog</v-btn>
      </v-toolbar-items>
      <v-spacer/>
      <v-toolbar-items>
        <v-btn class="white--text" color="purple darken-3" to="/categories.html">Categories</v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <v-container>
        <v-layout row wrap align-center>
          <v-flex>
            <component :is="layout"></component>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import HomeLayout from "./layouts/HomeLayout.vue";
import PostLayout from "./layouts/PostLayout.vue";
export default {
  components: { HomeLayout, PostLayout },
  computed: {
    layout() {
      return this.$page.frontmatter.layout || "HomeLayout";
    }
  }
};
</script>