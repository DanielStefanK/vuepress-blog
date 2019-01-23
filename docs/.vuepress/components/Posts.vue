<template>
  <v-container fluid grid-list-md>
    <v-layout row wrap>
      <v-flex xs12 sm6 lg3 v-for="post in posts" :key="post.path">
        <router-link :to="post.path">
          <p class="noUnderline">
            <v-img
              :aspect-ratio="16/9"
              :src="post.frontmatter.image"
              class="white--text gray elevation-3"
              height="200px"
            >
              <v-card-title>
                <div class="display-1 noUnderline">{{post.frontmatter.title}}</div>
              </v-card-title>
              <v-card-text class="white--text">{{post.frontmatter.description}}</v-card-text>
            </v-img>
          </p>
        </router-link>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  props: ["category"],
  computed: {
    posts() {
      let currentPage = this.page ? this.page : this.$page.path;
      let posts = this.$site.pages
        .filter(x => {
          return x.path.match(new RegExp(`(blog)(?=.*html)`));
        })
        .filter(x => {
          return this.category
            ? x.frontmatter.category
              ? x.frontmatter.category === this.category
              : false
            : true;
        })
        .sort((a, b) => {
          return new Date(b.frontmatter.date) - new Date(a.frontmatter.date);
        });
      return posts;
    }
  }
};
</script>


<style >
.gray img {
  filter: brightness(1%);
}
</style>
