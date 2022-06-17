<template>
  <div class="cat">
    <p class="cat__category">
      {{ category }}
    </p>
    <div class="cat__head">
      <p class="cat__title">Нямушка</p>
      <p class="cat__subtitle">с {{ filling }}</p>
    </div>
    <div class="cat__portions">
      <p class="cat__additional">{{ portions }} порций</p>
      <p class="cat__gift">
        {{ mouse }} {{ mouse === 1 ? "мышь" : mouse < 5 ? "мыши" : "мышей" }} в
        подарок
      </p>
    </div>
    <div class="cat__weight">{{ weight }} кг</div>
  </div>
</template>

<script>
export default {
  name: "FeedCat",
  props: ["category", "filling", "portions", "weight", "mouse"],
};
</script>

<style scoped lang="scss">
.cat {
  width: 320px;
  background-color: #f2f2f2;
  background-image: url("../assets/cat.jpg");
}
</style>
