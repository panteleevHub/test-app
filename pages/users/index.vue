<template>
  <section class="users container">
    <h1 class="users__title title">Пользователи</h1>
    <ul class="users__list list">
      <li v-for="user in users" class="users__item">
        <span class="users__name">{{ user.name }}</span>
        <span class="users__city">{{ user.address.city }}</span>
        <div class="users__links">
          <NuxtLink :to="`/users/${user.id}/albums`">Альбомы</NuxtLink>
          <NuxtLink :to="`/users/${user.id}/posts`">Посты</NuxtLink>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
  export default {
    async asyncData({ $axios }) {
      const users = await $axios.$get('https://jsonplaceholder.typicode.com/users');
      return { users };
    },
  }
</script>

<style lang="scss" scoped>
.users__title {
  text-align: center;
  margin-bottom: 25px;

  @media (min-width: $tablet-width) {
    margin-bottom: 35px;
  }

  @media (min-width: $desktop-width) {
    margin-bottom: 50px;
  }
}

.users__item {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  row-gap: 5px;
  background-color: $basic-yellow;
  border-radius: 10px;

  @media (min-width: $tablet-width) {
    padding: 15px;
  }
}

.users__name {
  font-weight: 500;
}

.users__links {
  display: flex;
  column-gap: 20px;
  padding-top: 5px;
}

.users__links a {
  color: $blue;
  text-decoration: underline;
}
</style>