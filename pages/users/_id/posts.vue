<template>
  <section class="posts container">
    <h1 class="posts__title title">Посты</h1>
    <div class="posts__link">
      <NuxtLink to="/users">Вернуться на главную</NuxtLink>
    </div>
    <ul class="posts__list list">
      <li v-for="post in posts" class="posts__item">
        <span class="posts__post-title">{{ post.title }}</span>
        <span>{{ post.body }}</span>
      </li>
    </ul>
  </section>
</template>

<script>
  export default {
    async asyncData({ params, $axios }) {
      const posts = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.id}/posts`);
      return { posts };
    },
  }
</script>

<style lang="scss" scoped>
.posts__title {
  text-align: center;
  margin-bottom: 15px;

  @media (min-width: $tablet-width) {
    margin-bottom: 25px;
  }

  @media (min-width: $desktop-width) {
    margin-bottom: 40px;
  }
}

.posts__item {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  row-gap: 10px;
  background-color: $basic-yellow;
  border-radius: 10px;

  @media (min-width: $tablet-width) {
    padding: 15px;
  }
}

.posts__post-title {
  font-weight: 500;
  text-align: center;
}

.posts__link {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 15px;

  @media (min-width: $tablet-width) {
    margin-bottom: 25px;
  }

  @media (min-width: $desktop-width) {
    margin-bottom: 40px;
  }
}

.posts__link a {
  color: $blue;
  text-decoration: underline;
}
</style>