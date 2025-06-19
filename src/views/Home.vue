<template>
  <main class="home wrapper">
    <h2>Photo Cards:</h2>
    <div class="grid">
      <Card
        v-for="(card, index) in cards"
        :key="index"
        :image="card.image"
        :text="card.text"
      />
    </div>
  </main>
</template>

<script setup>
import Card from '@/components/Card.vue';
import girlImage from '@/assets/girl.jpeg';
import pandaImage from '@/assets/panda.png';

// Định nghĩa danh sách cards
const cards = Array.from({ length: 28 }, (_, index) => ({
  image: [1, 3, 4, 11, 16, 17, 23, 25].includes(index) ? pandaImage : girlImage,
  text: 'Product name is quite long in some cases',
}));
</script>

<style scoped lang="scss">
.home {
  padding: 0 $spacingLarge $spacingLarge $spacingLarge;
  box-sizing: border-box;
  width: 100%;

  h2 {
    font-size: $fontSizeMedium;
    font-weight: bold;
    margin: 0 0 $spacingBase 0;
    @media (min-width: 992px) {
      font-size: $fontSizeLarge;
    }
  }

  .grid {
    display: grid;
    gap: $spacingBase;
    grid-template-columns: 1fr; /* 1 cột mặc định */
  }

  /* Màn hình từ 576px trở lên (tablet) */
  @media (min-width: $breakpointSm) {
    .grid {
      grid-template-columns: repeat(2, 1fr); /* 2 cột */
    }
  }
   @media (min-width: $breakpointMdSm) {
    .grid {
      grid-template-columns: repeat(3, 1fr); /* 3 cột */
    }
  }
  /* Màn hình từ 992px trở lên (desktop) */
  @media (min-width: $breakpointMd) {
    .grid {
      grid-template-columns: repeat(4, 1fr); /* 4 cột */
    }
  }

  /* Màn hình từ 1200px trở lên (large screen) */
  @media (min-width: $breakpointLg) {
    .grid {
      grid-template-columns: repeat(6, 1fr); /* 6 cột */
    }
  }
}
</style>