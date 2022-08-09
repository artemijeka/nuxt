<template>
  <div>
    <Tutorial />
    <nav>
      <h2>Articles</h2>
      <nuxt-link
        v-for="article in articles"
        :key="article.id"
        :to="{ name: 'articles-id', params: { id: article.id } }"
        class="main-page-nav__item"
      >
        {{ article.title }}
      </nuxt-link>
    </nav>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  data() {
    return {
      articles: [],
    }
  },
  head() {
    return {
      title: 'Nuxt + Vue + Vuex | Home page!',
      meta: [
        { name: 'twitter:title', content: 'Nuxt + Vue + Vuex | Home page!' },
        {
          name: 'twitter:description',
          content: 'Home page! Nuxt + Vue + Vuex = Power&Speed',
        },
        {
          name: 'twitter:image',
          content: 'https://i.ytimg.com/vi/yHrSHiBSP4U/maxresdefault.jpg',
        },
        { name: 'twitter:card', content: 'summary_large_image' },
      ],
    }
  },
  computed: {
    // posts() {
    //   return this.$store.state.posts.all
    // },
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/posts').then((response) => {
      this.articles = response.data
    })
    // fetch('https://jsonplaceholder.typicode.com/posts').then((response) => {
    //   response.json().then((articles) => {
    //     this.articles = articles
    //   })
    // })
  },
}
</script>

<style lang="scss">
.main-page-nav {
  &__item {
    margin-right: 10px;
  }
}
</style>
