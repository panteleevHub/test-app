<template>
  <section class="albums container">
    <h1 class="albums__title title">Альбомы</h1>
    <div class="albums__link">
      <NuxtLink to="/users">Вернуться на главную</NuxtLink>
    </div>
    <ul class="albums__list list">
      <li v-for="album in albums" class="albums__item">{{ album.title }}</li>
    </ul>
  </section>
</template>

<script>
  export default {
    async asyncData({ params, $axios }) {
      const albums = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.id}/albums`);
      return { albums };
    },
  }
</script>

<style lang="scss" scoped>
.albums__title {
  text-align: center;
  margin-bottom: 15px;

  @media (min-width: $tablet-width) {
    margin-bottom: 25px;
  }

  @media (min-width: $desktop-width) {
    margin-bottom: 40px;
  }
}

.albums__item {
  font-weight: 500;
  text-align: center;
  padding: 10px;
  background-color: $basic-yellow;
  border-radius: 10px;

  @media (min-width: $tablet-width) {
    padding: 15px;
  }
}

.albums__link {
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

.albums__link a {
  color: $blue;
  text-decoration: underline;
}
</style>