<template>
  <div class="card" @click="selectCat">
    <div
      class="cat"
      :style="[
        selected
          ? { border: '4px solid #d91667' }
          : { border: '4px solid #2ea8e6' },
        disabled ? { border: '4px solid #B3B3B3' } : {},
      ]"
      :class="{ catDissolve: disabled, disabled: disabled }"
      @mouseover="disabled ? {} : selected ? (catHovered = true) : {}"
      @mouseleave="catHovered = false"
    >
      <p class="cat__category pink" v-if="catHovered">Котэ не одобряет?</p>
      <p class="cat__category" v-else>
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
          <circle
            cx="40"
            cy="40"
            r="40"
            :fill="disabled ? '#B3B3B3' : fillColor"
          />
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
  <div class="card__text yellow" v-if="disabled">
    Печалька, с {{ filling }} закончился.
  </div>
  <template v-else>
    <div class="card__text" v-if="selected">
      {{ bottomText }}
    </div>
    <div class="card__text" v-else>
      Чего сидишь? Порадуй котэ,
      <span @click="selectCat" class="card__span">купи.</span>
    </div>
  </template>
</template>

<script>
import { ref } from "vue";

export default {
  name: "FeedCat",
  props: [
    "category",
    "filling",
    "portions",
    "weight",
    "mouse",
    "bottomText",
    "disabled",
  ],
  setup() {
    let count = ref(0);
    let fillColor = ref("#2EA8E6");
    let selected = ref(false);
    let catHovered = ref(false);
    const selectCat = () => {
      selected.value = !selected.value;
      selected.value
        ? (fillColor.value = "#D91667")
        : (fillColor.value = "#2EA8E6");
    };

    return {
      fillColor,
      count,
      selectCat,
      selected,
      catHovered,
    };
  },
};
</script>

<style scoped lang="scss">
$blue: #22a7e9;
$pink: #d91667;
$yellow: #ffff66;
.card {
  padding: 15px;
  overflow: hidden;
  &__text {
    text-align: center;
    font-weight: 400;
    font-size: 13px;
    line-height: 15px;
    color: #fff;
  }
  &__span {
    font-weight: 700;
    font-size: 13px;
    line-height: 15px;
    color: $blue;
    cursor: pointer;
  }
}

.yellow {
  color: $yellow;
}
.cat {
  position: relative;
  width: 320px;
  height: 480px;
  background-image: url("../assets/cat.png");
  background-color: #f2f2f2;
  background-position: bottom;
  background-repeat: no-repeat;
  border-radius: 12px;
  padding: 21px 48px;
  cursor: pointer;
  margin-bottom: 14px;
  &__selected {
    border: 4px solid $pink;
  }
  &__category {
    margin-bottom: 5px;
    font-weight: 400;
    font-size: 16px;
    line-height: 19px;
    color: #000;
  }
  &__title {
    font-weight: 700;
    font-size: 48px;
    line-height: 56px;
  }
  &__subtitle {
    font-weight: 700;
    font-size: 24px;
    line-height: 28px;
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
.catDissolve {
  background-image: url("../assets/cat_dissolve.png");
}
.pink {
  color: #e62e7a;
}
.disabled {
  color: #b3b3b3;
}
</style>
