<template>
  <div class="min-h-full bg-white">
    <main-navigation />
    <div>
      <slot>No Content</slot>
    </div>
  </div>
</template>

<script>
import MainNavigation from "~~/components/navigation/MainNavigation.vue";

export default {
  name: "Default",
  components: {
    MainNavigation,
  },
};
</script>

<style></style>
