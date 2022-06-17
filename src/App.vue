<template>
  <div class="container">
    <div class="app">
      <h1 class="app__title">Ты сегодня покормил кота?</h1>
      <ul class="app__cats">
        <li class="app__cat" v-for="cat in catsExample" :key="cat">
          <FeedCat
            :filling="cat.filling"
            :category="cat.category"
            :mouse="cat.mouse"
            :portions="cat.portions"
            :weight="cat.weight"
            :bottom-text="cat.bottomText"
            :disabled="cat.disabled"
          ></FeedCat>
        </li>
      </ul>
    </div>
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
        mouse: 1,
        weight: 0.5,
        bottomText: "Печень утки разварная с артишоками.",
        disabled: false,
      },
      {
        category: "Сказочное заморское яство",
        filling: "рыбой",
        portions: 40,
        mouse: 2,
        weight: 2,
        bottomText: "Головы щучьи с чесноком да свежайшая сёмгушка.",
        disabled: false,
      },
      {
        category: "Сказочное заморское яство",
        filling: "курой",
        portions: 100,
        mouse: 5,
        weight: 5,
        bottomText: "Филе из цыплят с трюфелями в бульоне.",
        disabled: true,
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
@import url("https://fonts.googleapis.com/css2?family=Alegreya+Sans:wght@400;700&family=Exo+2:wght@100&family=Roboto&display=swap");
* {
  box-sizing: border-box;
}
p {
  margin: 0;
}
body {
  font-family: "Alegreya Sans", sans-serif;
  background-image: url("assets/pattern.jpg");
}
.container {
  max-width: 1120px;
  margin: 0 auto;
}
.app {
  &__title {
    font-family: "Exo 2", sans-serif;
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
