<template>
  <nav>
    <router-link to="/">Home</router-link> |
  </nav>
  <router-view/>
</template>

<script>
  export default {
data() {
  return {
 name: process.env.VUE_APP_NAME,
  };
},
};
</script>

<style lang="scss">
@import "bootstrap";
</style>
