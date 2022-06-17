<template>
  <div class="container">
    <h1 class="app__title">Ты сегодня покормил кота?</h1>
    <ul class="app__cats">
      <li class="app__cat"></li>
    </ul>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Exo+2:wght@100&family=Roboto&display=swap");
body {
  font-family: "Exo 2", sans-serif;
  background-image: url("assets/pattern.jpg");
}
.container {
  max-width: 1120px;
  margin: 0 auto;
}
.app {
  &__title {
    padding-top: 36px;
    text-align: center;
    font-size: 36px;
    line-height: 44px;
    color: #fff;
  }
}
</style>
