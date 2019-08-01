// components/Footer.vue
<template>
  <footer>
    Copyright {{ getCurrentYear }} by
    <a v-bind:href="href">Gaylon Alfano</a>
  </footer>
</template>

<script>
export default {
  data: () => ({
    href: "http://gaylonalfano.com"
  }),
  computed: {
    getCurrentYear() {
      return new Date().getFullYear();
    }
  }
};
</script>

<style>
footer {
  text-align: center;
  color: #00a672;
  letter-spacing: 0.5px;
  padding: 20px;
}
</style>