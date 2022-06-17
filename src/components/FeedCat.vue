<template>
  <div class="polygon">
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
          {{ mouse > 1 ? mouse : "" }}
          {{ mouse === 1 ? "мышь" : mouse < 5 ? "мыши" : "мышей" }} в подарок
        </p>
      </div>
      <div class="cat__weight">
        <svg
          width="80"
          height="80"
          viewBox="0 0 80 80"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <circle cx="40" cy="40" r="40" fill="#2EA8E6" />
        </svg>
        <div class="cat__desc">
          <p class="cat__weigh">
            {{ weight }}
          </p>
          <p class="cat__measure">кг</p>
        </div>
      </div>
    </div>
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
  position: relative;
  width: 320px;
  height: 480px;
  background-color: #f2f2f2;
  background-image: url("../assets/cat.jpg");
  background-position: bottom;
  background-repeat: no-repeat;
  border: 4px solid #2ea8e6;
  border-radius: 12px;
  padding: 21px 48px;
  &__category {
    margin-bottom: 5px;
    font-weight: 400;
    font-size: 16px;
    line-height: 19px;
    color: #666666;
  }
  &__title {
    font-weight: 700;
    font-size: 48px;
    line-height: 56px;
    color: #000;
  }
  &__subtitle {
    font-weight: 700;
    font-size: 24px;
    line-height: 28px;
    color: #000;
  }
  &__head {
    margin-bottom: 15px;
  }
  &__weight {
    position: absolute;
    display: flex;
    flex-direction: column;
    align-items: center;
    bottom: 0;
    right: 0;
    padding-right: 12px;
    padding-bottom: 12px;
  }
  &__desc {
    position: absolute;
    text-align: center;
    top: 20%;
  }
  &__weigh {
    font-weight: 400;
    font-size: 42px;
    line-height: 22px;
    color: #fff;
    margin-bottom: 8px;
  }
  &__measure {
    font-weight: 400;
    font-size: 21px;
    line-height: 22px;
    color: #fff;
  }
}
</style>
