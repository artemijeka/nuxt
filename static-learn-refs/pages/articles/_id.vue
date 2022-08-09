<script>
import axios from 'axios';

export default {
  data() {
    return {
      id: this.$route.params.id,
      article: {},
      /* move to the store posts: */
      // posts: [
      // {
      //   id: 'one',
      //   title: '1 Заголовок',
      //   text: '1 Далеко-далеко за, словесными горами в стране гласных и согласных живут рыбные тексты. Его семантика толку раз силуэт вершину, подпоясал последний которой дал домах маленький она, семь моей предложения щеке снова они, по всей даль! Возвращайся букв грамматики продолжил свою текст. Продолжил его над бросил вопрос даже последний города на берегу сбить большой текстами своих имени, себя назад там заманивший, которой обеспечивает приставка диких ручеек великий, алфавит букв. Домах на берегу власти собрал скатился он алфавит курсивных маленькая составитель текста, вопроса буквоград инициал злых океана семь, рыбными предложения реторический предупреждал, страна большого свою что деревни запятой грустный решила. Запятой взобравшись использовало дорогу? Алфавит домах все свою.',
      // },
      // {
      //   id: 'two',
      //   title: '2 Заголовок',
      //   text: '2 Далеко-далеко за, словесными горами в стране гласных и согласных живут рыбные тексты. Его семантика толку раз силуэт вершину, подпоясал последний которой дал домах маленький она, семь моей предложения щеке снова они, по всей даль! Возвращайся букв грамматики продолжил свою текст. Продолжил его над бросил вопрос даже последний города на берегу сбить большой текстами своих имени, себя назад там заманивший, которой обеспечивает приставка диких ручеек великий, алфавит букв. Домах на берегу власти собрал скатился он алфавит курсивных маленькая составитель текста, вопроса буквоград инициал злых океана семь, рыбными предложения реторический предупреждал, страна большого свою что деревни запятой грустный решила. Запятой взобравшись использовало дорогу? Алфавит домах все свою.',
      // },
      // {
      //   id: 'three',
      //   title: '3 Заголовок',
      //   text: '3 Далеко-далеко за, словесными горами в стране гласных и согласных живут рыбные тексты. Его семантика толку раз силуэт вершину, подпоясал последний которой дал домах маленький она, семь моей предложения щеке снова они, по всей даль! Возвращайся букв грамматики продолжил свою текст. Продолжил его над бросил вопрос даже последний города на берегу сбить большой текстами своих имени, себя назад там заманивший, которой обеспечивает приставка диких ручеек великий, алфавит букв. Домах на берегу власти собрал скатился он алфавит курсивных маленькая составитель текста, вопроса буквоград инициал злых океана семь, рыбными предложения реторический предупреждал, страна большого свою что деревни запятой грустный решила. Запятой взобравшись использовало дорогу? Алфавит домах все свою.',
      // },
      // ],
    }
  },
  head() {
    return {
      title: this.article.title,
      meta: [
        { name: 'twitter:title', content: this.article.title },
        { name: 'twitter:description', content: this.article.text },
        { name: 'twitter:image', content: this.article.image },
        { name: 'twitter:card', content: 'summary_large_image' },
      ],
    }
  },
  computed: {
    post() {
      return this.$store.state.articles.all.find((article) => article.id === this.id)
    },
    relatedArtices() {
      return this.$store.state.articles.all.filter((article) => article.id !== this.id)
    },
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/posts/' + this.id).then(response=>{
     this.article = response.data
    })
    // fetch('https://jsonplaceholder.typicode.com/posts/' + this.id).then(
    //   (response) => {
    //     response.json().then((article) => {
    //       this.article = article
    //     })
    //   }
    // )
  },
}
</script>

<template>
  <div class="post-page">
    <main class="post-page__post">
      <h1>{{ article.title }}</h1>
      <p>
        {{ article.body }}
      </p>
      <img
        class="post-page__post-img"
        :src="article.image"
        :alt="article.title"
        :title="article.title"
      />
    </main>
    <aside class="post-page__aside">
      <ul>
        <li
          v-for="related in relatedArticles"
          :key="related.id"
          class="post-page__aside-item"
        >
          <!-- Для переключения без перезагрузки -->
          <nuxt-link :to="`/posts/${related.id}`">{{
            related.title
          }}</nuxt-link>

          <!-- Или -->
          <!-- <nuxt-link :to="{ name: 'posts-id', params: {id: related.id} }">{{ related.title }}</nuxt-link> -->

          <!-- Обычный метод с перезагрузкой страницы: -->
          <!-- <a :href="`/posts/${related.id}`">{{ related.title }}</a> -->
        </li>
      </ul>
    </aside>
  </div>
</template>

Не инкапсулированные стили в стиле именования BEM
<style lang="scss">
.post-page {
  display: flex;
  &__post {
    width: 70%;
    &-img {
      width: 50%;
    }
  }
  &__aside {
    width: 30%;
    display: flex;
    align-items: center;
    justify-content: center;
    &-item {
      list-style-type: none;
      margin-bottom: 5px;
    }
  }
}
</style>
