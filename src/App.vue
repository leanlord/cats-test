<template>
  <div class="container">
    <h1 class="app__title">Ты сегодня покормил кота?</h1>
    <ul class="app__cats">
      <li class="app__cat" v-for="cat in catsExample" :key="cat">
        <FeedCat
          :filling="cat.filling"
          :category="cat.category"
          :mouse="cat.mouse"
          :portions="cat.portions"
          :weight="cat.weight"
        ></FeedCat>
      </li>
    </ul>
  </div>
</template>

<script>
import FeedCat from "@/components/FeedCat";
export default {
  components: { FeedCat },
  setup() {
    const catsExample = [
      {
        category: "Сказочное заморское яство",
        filling: "фуа-гура",
        portions: 10,
        mouse: 3,
        weight: 0.5,
      },
    ];
    return {
      catsExample,
    };
  },
};
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
  &__cats {
    display: flex;
    justify-content: space-between;
  }
}
</style>
