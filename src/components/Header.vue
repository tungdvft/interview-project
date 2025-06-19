<template>
  <header class="site-header">
    <div class="wrapper header-content">
      <div class="logo-title">
        <img :src="logo" alt="Logo" />
      </div>
      <nav class="menu" :class="{ 'menu-open': isMenuOpen }">
        <button class="hamburger" @click="toggleMenu"></button>
        <div class="menu-items">
          <a href="#indie-game">Indie Game</a>
          <a href="#entry-game">Entry Game</a>
          <a href="#community">Community</a>
        </div>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue';
import logo from '@/assets/logo.png';

// Quản lý trạng thái menu
const isMenuOpen = ref(false);

// Hàm toggle menu
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style lang="scss" scoped>
@use 'sass:color';

.site-header {
  background-color: $primaryColor;
  padding: $spacingSmall 0;
  width: 100%;
  box-sizing: border-box;

  .header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 $spacingBase;
    width: 100%;
    box-sizing: border-box;
  }

  .logo-title {
    display: flex;
    align-items: center;
    gap: $spacingSmall;
    color: $white;
    font-weight: 600;
    font-size: $fontSizeSmall;
  }

  .menu {
    display: flex;
    align-items: center;

    .hamburger {
      display: block;
      background: none;
      border: none;
      color: $white;
      font-size: $fontSizeLarge;
      cursor: pointer;
      position: relative;
      width: $spacingLarge;
      height: $spacingLarge;

      &:before {
        content: '☰';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
      }
    }

    &.menu-open .hamburger:before {
      content: '✕';
    }

    .menu-items {
      display: none;
      flex-direction: column;
      position: absolute;
      top: calc(#{$spacingLarge} + #{$spacingBase});
      right: 0;
      background-color: $primaryColor;
      padding: $spacingBase;
      width: 100%;
      box-shadow: $boxShadowHover;
      z-index: 10;
      transition: all 0.3s ease;
      gap: $spacingBase; /* Khoảng cách 16px giữa các mục menu (mobile) */

      a {
        padding: $spacingSmall $spacingBase;
        border: 1px solid $white;
        background-color: transparent;
        color: $white;
        font-size: $fontSizeSmall;
        border-radius: $borderRadius;
        cursor: pointer;
        text-decoration: none;
        display: block;
        transition: background-color 0.2s ease;

        &:hover {
          background-color: color.adjust($primaryColor, $lightness: -10%);
        }
      }
    }

    &.menu-open .menu-items {
      display: flex;
    }
  }

  /* Tablet và lớn hơn */
  @media (min-width: $breakpointSm) {
    .header-content {
      padding: 0 $spacingLarge;
    }

    .logo-title {
      font-size: $fontSizeBase;
    }

    .menu .menu-items {
      width: 200px;
    }
  }

  /* Desktop */
  @media (min-width: $breakpointMd) {
    .menu {
      .hamburger {
        display: none;
      }

      .menu-items {
        display: flex;
        flex-direction: row;
        position: static;
        width: auto;
        padding: 0;
        background-color: transparent;
        box-shadow: none;
        gap: $spacingBase; /* Khoảng cách 16px giữa các mục menu (desktop) */

        a {
          display: inline-block;
        }
      }
    }
  }

  /* Desktop lớn */
  @media (min-width: $breakpointLg) {
    .header-content {
      padding: 0 $spacingXLarge;
    }

    .logo-title {
      font-size: $fontSizeMedium;
    }

    .menu .menu-items a {
  
      font-size: $fontSizeBase;
    }
  }
}
</style>