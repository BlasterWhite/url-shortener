<script setup lang="ts"></script>

<template>
  <nav class="navbar">
    <router-link to="/">Home</router-link>
    <router-link to="/">About</router-link>
  </nav>
</template>

<style lang="scss" scoped>
  .navbar {
    padding: 1rem;
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: center;
    gap: 2rem;

    a {
      color: #130e3d;
      text-decoration: none;
      font-size: 1.2em;
      font-weight: 600;

      &::after {
        content: '';
        display: block;
        width: 0;
        height: 2px;
        background: #80da37;
        transition: width 0.3s;
      }

      &:hover::after {
        width: 100%;
      }
    }
  }
</style>
