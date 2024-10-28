<template>
</template>

<script>
  export default {
    middleware({ store, redirect }) {
      redirect('/users')
    }
  }
</script>
