<template>
  <div>
    <nav>
      <nuxt-link to="/">Main</nuxt-link>
      <!-- Или: -->
      <!-- <nuxt-link :to="{name: 'index'}">Main</nuxt-link> -->

      <nuxt-link to="/test">Test</nuxt-link>
      <nuxt-link to="/posts/one">Post one</nuxt-link>
      <nuxt-link to="/posts/two">Post two</nuxt-link>
      <nuxt-link to="/posts/three">Post three</nuxt-link>

      <!-- Классические с перезагрузкой страницы: -->
      <!-- <a href="/">Main</a>
      <a href="/test">Test</a>
      <a href="/posts/one">Post one</a>
      <a href="/posts/two">Post two</a>
      <a href="/posts/three">Post three</a> -->
    </nav>
  </div>
</template>



Инкапсулированные стили "scoped" 
<style scoped lang="scss">
  nav a {
    margin-right: 10px;
  }
</style>