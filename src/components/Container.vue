<script setup>
import Card from "./Card.vue";
import Slider from "./Slider.vue";
import OverviewCard from "./OverviewCard.vue";

const prefersDarkScheme = window.matchMedia("(prefers-color-scheme: dark)");

const handleChangeTheme = (e) => {
  if (prefersDarkScheme.matches) {
    document.body.classList.toggle("light-theme");
  } else {
    document.body.classList.toggle("dark-theme");
  }
};

const cards = [
  {
    id: 1,
    author: "@nathanf",
    socialName: "facebook",
    quantity: "1987",
    quantityText: "Followers",
    iconUrl: "/src/assets/icon-facebook.svg",
    brandColor: "#198ff5",
    statistic: 12,
  },
  {
    id: 2,
    author: "@nathanf",
    socialName: "twitter",
    quantity: "1044",
    quantityText: "Followers",
    iconUrl: "/src/assets/icon-twitter.svg",
    brandColor: "#1ca0f2",
    statistic: 99,
  },
  {
    id: 3,
    author: "@realnathanf",
    socialName: "instagram",
    quantity: "11k",
    quantityText: "Followers",
    iconUrl: "/src/assets/icon-instagram.svg",
    brandColor: "linear-gradient(to right, #fdc468, #df4996)",
    statistic: 1099,
  },
  {
    id: 4,
    author: "@Nathan F.",
    socialName: "youtube",
    quantity: "8239",
    quantityText: "Subscribers",
    iconUrl: "/src/assets/icon-youtube.svg",
    brandColor: "#c4032a",
    statistic: -144,
  },
];

const overview = [
  {
    id: 1,
    measureText: "Page View",
    quantity: "87",
    iconUrl: "/src/assets/icon-facebook.svg",
    statistic: 3,
  },
  {
    id: 2,
    measureText: "Likes",
    quantity: "52",
    iconUrl: "/src/assets/icon-facebook.svg",
    statistic: -2,
  },
  {
    id: 3,
    measureText: "Likes",
    quantity: "5462",
    iconUrl: "/src/assets/icon-instagram.svg",
    statistic: 2257,
  },
  {
    id: 4,
    measureText: "Profile Views",
    quantity: "52k",
    iconUrl: "/src/assets/icon-instagram.svg",
    statistic: 1375,
  },
  {
    id: 5,
    measureText: "Retweets",
    quantity: "117",
    iconUrl: "/src/assets/icon-twitter.svg",
    statistic: 303,
  },
  {
    id: 6,
    measureText: "Likes",
    quantity: "507",
    iconUrl: "/src/assets/icon-twitter.svg",
    statistic: 553,
  },
  {
    id: 7,
    measureText: "Likes",
    quantity: "107",
    iconUrl: "/src/assets/icon-youtube.svg",
    statistic: -19,
  },
  {
    id: 8,
    measureText: "Total Views",
    quantity: "1407",
    iconUrl: "/src/assets/icon-youtube.svg",
    statistic: -12,
  },
];
</script>

<template>
  <header>
    <div class="header__title">
      <span>Social Media Dashboard</span>
      <span>Total Followers: 23,004</span>
    </div>
    <hr class="divider" />

    <div class="header__switcher">
      <span>Dark Mode</span>
      <Slider
        @change="handleChangeTheme"
        :initialValue="prefersDarkScheme.matches"
      />
    </div>
  </header>
  <section>
    <div class="cards">
      <Card
        v-for="card of cards"
        :key="card.id"
        :quantity="card.quantity"
        :quantityText="card.quantityText"
        :author="card.author"
        :iconUrl="card.iconUrl"
        :brandColor="card.brandColor"
        :statistic="card.statistic"
      />
    </div>
  </section>
  <section class="section-overview">
    <h1>Overview - Today</h1>
    <div class="cards">
      <OverviewCard
        v-for="card of overview"
        :key="card.id"
        :measureText="card.measureText"
        :quantity="card.quantity"
        :iconUrl="card.iconUrl"
        :statistic="card.statistic"
      />
    </div>
  </section>
</template>

<style scoped>
header {
  display: flex;
  flex-direction: column;

  margin-bottom: 30px;
}

.header__title {
  display: flex;
  flex-direction: column;
  font-weight: 700;
  line-height: 1.5;
}

.header__title span:nth-child(1) {
  font-size: 24px;
  font-weight: 700;
}

.header__title span:nth-child(2) {
  font-size: 14px;
}

.divider {
  border-top: 1px solid #000;
  width: 100%;
  margin: 15px 0;
}

.header__switcher {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header__switcher span {
  font-size: 14px;
  font-weight: bold;
}

.cards {
  display: grid;
  justify-content: center;
  gap: 20px;
}

.section-overview h1 {
  font-size: 24px;
}
</style>
