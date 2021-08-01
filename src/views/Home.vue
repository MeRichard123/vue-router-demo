<template>
  <section class="home">
    <h1>Landing Page</h1>
  </section>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
};
</script>
<style scoped>
.home{
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-image: url('../assets/wallpaper.jpg');
  background-size: cover;
  background-position: center;
}
</style>
