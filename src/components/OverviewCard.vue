<script setup>
import { computed } from "vue";

const props = defineProps({
  measureText: String,
  quantity: String,
  iconUrl: String,
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
</script>

<template>
  <div class="overview-card">
    <div class="info">
      <div>{{ measureText }}</div>
      <div>{{ quantity }}</div>
    </div>
    <div class="statistics">
      <img :src="iconUrl" />
      <div>
        <img :src="statisticIcon" alt="icon-up" />
        <span :style="{ color: statisticTextColor }">{{ statistic }}%</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.overview-card {
  background: var(--color-cardBG);
  border-radius: 4px;

  width: 335px;
  height: 120px;
  padding: 25px;

  display: flex;
  align-items: center;
  justify-content: space-between;
}

.overview-card .info,
.overview-card .statistics {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
}

.overview-card .info {
  align-items: flex-start;
}

.overview-card .statistics {
  align-items: flex-end;
  font-size: 12px;
  font-weight: 700;
}

.overview-card .statistics div {
  display: flex;
  align-items: center;
  gap: 5px;
}

.overview-card .info div {
  font-weight: bold;
}
.overview-card .info div:nth-child(1) {
  font-size: 14px;
}

.overview-card .info div:nth-child(2) {
  font-size: 32px;
}
</style>
