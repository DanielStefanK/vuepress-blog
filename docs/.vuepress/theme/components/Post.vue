
<template>
  <v-hover>
    <v-card slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 2}`">
      <v-card flat>
        <v-parallax :src="$page.frontmatter.image" height="300">
          <v-layout column fill-height align-center justify-center>
            <v-card-title class="white--text">
              <div class="display-1">{{$page.frontmatter.title}}</div>
            </v-card-title>
          </v-layout>
        </v-parallax>
      </v-card>
      <v-card-text>
        <article>
          <Content/>
        </article>
      </v-card-text>
    </v-card>
  </v-hover>
</template>

