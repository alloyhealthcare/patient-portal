<template>
  <div class="min-h-full bg-white">
    <main-navigation />
    <patient-header />
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-8">
      <slot>No Content</slot>
    </div>
  </div>
</template>

<script>
import MainNavigation from "~~/components/navigation/MainNavigation.vue";
import PatientHeader from "../components/navigation/headers/PatientHeader.vue";

export default {
  name: "Default",
  components: {
    MainNavigation,
    PatientHeader,
  },
};
</script>

<style></style>
