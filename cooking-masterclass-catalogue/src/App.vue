<script setup>
import { ref, computed } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

const wishlist = ref([]);

const instructors = ref([
  {
    id: 1,
    name: "Chef Yara Mizrahi",
    title: "Shakshuka Masterclass",
    price: 1619.99, // was $89.99
    level: "Beginner",
    soldOut: false,
    img: "https://i.ibb.co/n8cLtnNt/shakshuka-146.webp",
    bio: "James Beard Award-winning chef from Tel Aviv. Yara teaches you to master Middle Eastern cuisine with confidence.",
    tags: [
      "Elevate Your Cooking Skills & Techniques",
      "Make The Most Of Your Ingredients",
      "Refine Your Beef, Chicken, & Meat Dishes",
    ],
  },
  {
    id: 2,
    name: "Chef Leo Vance",
    title: "Smoothie & Raw Cuisine",
    price: 899.99, // was $49.99
    level: "Beginner",
    soldOut: false,
    img: "https://cdn.apartmenttherapy.info/image/upload/f_auto,q_auto:low,c_fill,g_auto,w_1460,h_1460/tk%2Fphoto%2F2025%2F12-2025%2F2025-12-pineapple-smoothie%2Fpineapple-smoothie-230",
    bio: "Wellness chef and nutritionist. Leo shows you how to craft nutritious, flavorful meals that energize your day.",
    tags: [
      "Craft Nutritious Flavorful Meals",
      "Create Healthy & Tasty Vegetarian Meals",
    ],
  },
  {
    id: 3,
    name: "Chef Sofia Romano",
    title: "Perfect Frittata",
    price: 1259.99, // was $69.99
    level: "Intermediate",
    soldOut: true,
    img: "https://i.ibb.co/JFmCbrwP/k-archive-b64b093135fdd1e636b74d0520872920fcd8829a.jpg",
    bio: "Italian nonna-trained chef. Sofia’s 20-minute techniques will change your weeknight dinners forever.",
    tags: ["Bake Delicious Bread & Pastries", "Elevate Everyday Cuisine"],
  },
  {
    id: 4,
    name: "Chef Marcus Chen",
    title: "Copycat Egg Bites",
    price: 1439.99, // was $79.99
    level: "Advanced",
    soldOut: false,
    img: "https://cdn.apartmenttherapy.info/image/upload/f_auto,q_auto:low,c_fill,g_auto,w_1460,h_1460/tk%2Fphoto%2F2025%2F12-2025%2F2025-12-egg-bites-starbucks%2Fegg-bites-starbucks-448",
    bio: "Former Starbucks R&D chef. Marcus reverse-engineers the custardy, cheesy egg bites you love.",
    tags: [
      "Elevate Everyday Cuisine",
      "Pair Wines, Mix Cocktails, & Brew Coffee",
    ],
  },
  {
    id: 5,
    name: "Chef Elena Kosta",
    title: "Greek Salmon Patties",
    price: 1709.99, // was $94.99
    level: "Intermediate",
    soldOut: false,
    img: "https://cdn.apartmenttherapy.info/image/upload/f_auto,q_auto:low,c_fill,g_auto,w_1460,h_1460/tk%2Fphoto%2F2025%2F12-2025%2F2025-12-greek-salmon-patties%2Fgreek-salmon-patties-161",
    bio: "The 7x James Beard Award-winning cookbook author embraces the vast diversity of Mediterranean cuisine.",
    tags: [
      "Explore Global Cuisine",
      "Elevate Your Cooking Skills & Techniques",
      "Make The Most Of Your Ingredients",
    ],
  },
]);

const wishlistCount = computed(() => wishlist.value.length);

function toggleWishlist(id) {
  const index = wishlist.value.indexOf(id);
  if (index > -1) {
    wishlist.value.splice(index, 1);
  } else {
    wishlist.value.push(id);
  }
}

function isSaved(id) {
  return wishlist.value.includes(id);
}

function formatPrice(price) {
  return new Intl.NumberFormat("en-ZA", {
    style: "currency",
    currency: "ZAR",
  }).format(price);
}
</script>

<template>
  <div class="app">
    <header class="main-header">
      <div class="header-inner">
        <img src="@/assets/logo.svg" alt="Logo" class="logo" />
        <h2 class="brand">MasterClass</h2>
        <HelloWorld :wishlist-count="wishlistCount" />
      </div>
    </header>

    <main class="content">
      <section class="instructor-section">
        <h1 class="section-title">
          {{ instructors.length }} Food & Drink Instructors
        </h1>

        <div class="carousel-wrapper">
          <div class="card-carousel">
            <div
              v-for="instructor in instructors"
              :key="instructor.id"
              class="instructor-card"
              :class="{ 'sold-out': instructor.soldOut }"
            >
              <div class="card-img-wrapper">
                <img :src="instructor.img" :alt="instructor.name" />
                <div v-if="instructor.soldOut" class="sold-out-overlay">
                  Sold Out
                </div>
              </div>

              <div class="card-body">
                <div class="text-effects">
                  <h2 class="glowing-text" :data-t="instructor.name">
                    {{ instructor.name }}
                  </h2>
                  <div class="gradient"></div>
                  <div class="spotlight"></div>
                </div>

                <p class="bio">{{ instructor.bio }}</p>

                <div class="tags">
                  <span v-for="tag in instructor.tags" :key="tag" class="tag">
                    {{ tag }}
                  </span>
                </div>

                <div class="card-footer">
                  <div class="meta">
                    <span class="price">{{
                      formatPrice(instructor.price)
                    }}</span>
                    <span class="level">{{ instructor.level }}</span>
                  </div>
                  <button
                    v-if="!instructor.soldOut"
                    @click="toggleWishlist(instructor.id)"
                    :class="{ saved: isSaved(instructor.id) }"
                    class="save-btn"
                  >
                    {{ isSaved(instructor.id) ? "❤ Saved" : "♡ Save" }}
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<style scoped>
.app {
  background: #0a0a0a;
  color: #fff;
  min-height: 100vh;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.main-header {
  background: #141414;
  border-bottom: 1px solid #2a2a2a;
  padding: 1rem 2rem;
  position: sticky;
  top: 0;
  z-index: 100;
}

.header-inner {
  max-width: 1600px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.logo {
  width: 32px;
  height: 32px;
  filter: brightness(0) invert(1);
}

.brand {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0;
}

.content {
  max-width: 1600px;
  margin: 0 auto;
  padding: 3rem 2rem;
}

.instructor-section {
  text-align: center;
}

.section-title {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 2rem;
  text-align: center;
}

.carousel-wrapper {
  display: flex;
  justify-content: center;
}

.card-carousel {
  display: inline-flex;
  gap: 1.5rem;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  padding-bottom: 1rem;
  max-width: 100%;
}

.card-carousel::-webkit-scrollbar {
  height: 8px;
}
.card-carousel::-webkit-scrollbar-track {
  background: #1a1a1a;
  border-radius: 4px;
}
.card-carousel::-webkit-scrollbar-thumb {
  background: #444;
  border-radius: 4px;
}

.instructor-card {
  flex: 0 0 380px;
  background: #1a1a1a;
  border-radius: 12px;
  overflow: hidden;
  scroll-snap-align: start;
  transition: transform 0.3s;
  text-align: left;
}

.instructor-card:hover {
  transform: scale(1.02);
}

.instructor-card.sold-out {
  opacity: 0.5;
}

.card-img-wrapper {
  position: relative;
  width: 100%;
  height: 220px;
}

.card-img-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.sold-out-overlay {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  font-weight: 700;
  text-transform: uppercase;
}

.card-body {
  padding: 1.5rem;
}

.bio {
  color: #b3b3b3;
  font-size: 0.95rem;
  line-height: 1.5;
  margin: 1rem 0 1.5rem;
  min-height: 60px;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tag {
  background: #2a2a2a;
  color: #e5e5e5;
  padding: 0.4rem 0.8rem;
  border-radius: 4px;
  font-size: 0.75rem;
  font-weight: 500;
}

.card-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 1rem;
  border-top: 1px solid #2a2a2a;
}

.meta {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.price {
  color: #ff6b35;
  font-size: 1.25rem;
  font-weight: 700;
}

.level {
  color: #888;
  font-size: 0.8rem;
  text-transform: uppercase;
}

.save-btn {
  background: #e50914;
  color: white;
  border: none;
  padding: 0.6rem 1.2rem;
  border-radius: 4px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}

.save-btn:hover {
  background: #f6121d;
  transform: scale(1.05);
}

.save-btn.saved {
  background: #333;
  color: #ff6b35;
}

.text-effects {
  position: relative;
  overflow: hidden;
  margin-bottom: 0.5rem;
}

.glowing-text {
  position: relative;
  background: black;
  color: transparent;
  text-align: left;
  margin: 0;
  padding: 0.5rem 0;
  font-size: 1.4rem;
  font-weight: 700;
}
.glowing-text::before,
.glowing-text::after {
  content: attr(data-t);
  color: white;
  filter: blur(0.02em);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  pointer-events: none;
}
.glowing-text::after {
  mix-blend-mode: difference;
}
.gradient,
.spotlight {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  pointer-events: none;
  z-index: 10;
}
.gradient {
  background: linear-gradient(45deg, purple, blue);
  mix-blend-mode: multiply;
}
.spotlight {
  animation: light 5s linear infinite;
  background:
    radial-gradient(circle, white, transparent 25%) 0 0 / 25% 25%,
    radial-gradient(circle, white, black 25%) 50% 50% / 12.5% 12.5%;
  top: -100%;
  left: -100%;
  mix-blend-mode: color-dodge;
}
@keyframes light {
  100% {
    transform: translate3d(50%, 50%, 0);
  }
}

@media (max-width: 768px) {
  .instructor-card {
    flex: 0 0 300px;
  }
  .content {
    padding: 2rem 1rem;
  }
}
</style>
