<template>
  <router-link to="#" class="card">
    <div class="image-wrapper">
      <img :src="image" alt="Card image" />
    </div>
    <h3>{{ text }}</h3>
  </router-link>
</template>

<script setup>
import { RouterLink } from 'vue-router';
defineProps({
  image: String,
  text: String,
});
</script>

<style scoped lang="scss">
.card {
  background-color: $white;
  box-shadow: $boxShadow;
  width: 100%;
  display: block;
  text-decoration: none;
  color: inherit;
  border-radius: $borderRadius;
  transition: box-shadow 0.2s ease;
  padding-bottom: 1rem;

  .image-wrapper {
    width: 100%;
    padding-top: 66.6667%; /* Tỉ lệ 3:2 */
    position: relative;
    overflow: hidden;

    img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  h3 {
    font-weight: bold;
    font-size: $fontSizeSmall;
    padding: $spacingSmall;
    color: $textColor;
    line-height: 1.4;
    max-height: calc(1rem * 1.4 * 2); /* 2 dòng */
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 2;
    line-clamp: 2;
    transition: color 0.2s ease;
    margin: 0;
  }

  &:hover {
    box-shadow: $boxShadowHover;

    h3 {
      color: $primaryColor;
    }
  }
}
</style>