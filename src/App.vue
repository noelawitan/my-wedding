<template>
  <the-nav-bar></the-nav-bar>
  <the-dashboard></the-dashboard>

  <the-footer></the-footer>
</template>

<script>
import TheNavBar from '@/components/TheNavBar.vue';
import TheDashboard from "@/components/TheDashboard.vue";
import TheFooter from '@/components/TheFooter.vue';

export default {
  components: {
    TheNavBar,
    TheDashboard,
    TheFooter
  }
}
</script>
<style>
body {
  font-family: "Gotham SSm", Helvetica, Arial, sans-serif;
}
</style>