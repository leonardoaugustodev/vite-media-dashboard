<script setup>
import { computed, ref } from "vue";

const props = defineProps({
  quantity: String,
  quantityText: String,
  author: String,
  iconUrl: String,
  brandColor: String,
  statistic: Number,
});

const statisticIcon = computed(() => {
  const iconName = props.statistic > 0 ? "up" : "down";

  return `/src/assets/icon-${iconName}.svg`;
});

const statisticTextColor = computed(() => {
  return props.statistic > 0
    ? "var(--color-primary-limeGreen)"
    : "var(--color-primary-brightRed)";
});

const borderTopColorVars = computed(() => {
  return { "--borderColor": props.brandColor };
});

console.log(statisticIcon.value);
</script>

<template>
  <div class="card" :style="borderTopColorVars">
    <div class="card__author">
      <img :src="iconUrl" />
      <span>{{ author }}</span>
    </div>
    <div class="card__content">
      <div class="card__quantity">{{ quantity }}</div>
      <span class="">{{ quantityText }}</span>
    </div>
    <div class="card__statistics">
      <img :src="statisticIcon" alt="icon-up" />
      <span :style="{ color: statisticTextColor }">{{ statistic }} Today</span>
    </div>
  </div>
</template>

<style scoped>
.card {
  background: var(--color-cardBG);

  width: 335px;
  height: 220px;

  padding: 20px;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;

  border-radius: 4px;

  position: relative;
}

.card::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 4px;
  background: var(--borderColor);
  border-radius: 4px 4px 0 0;
  top: 0px;
  left: 0;
}

.card__author,
.card__statistics {
  display: flex;
  gap: 5px;
  align-items: center;

  font-size: 12px;
  font-weight: 700;
}

.card__quantity {
  font-size: 54px;
  font-weight: 700;
}

.card__content {
  display: flex;
  flex-direction: column;
  align-items: center;

  text-transform: uppercase;
}

.card__content span {
  font-size: 14px;
  letter-spacing: 3px;
}

.social-facebook {
}
</style>
