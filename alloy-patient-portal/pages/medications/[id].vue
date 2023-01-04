<template>
  <NuxtLayout> Medication {{ $route.params.id }} </NuxtLayout>
</template>

<script setup>
const client = useSupabaseClient();

const { data: medications } = await useAsyncData("medications", async () => {
  const { data } = await client.from("medications").select();
  return data;
});
</script>

<script>
export default {
  name: "Medication Detail",
};
</script>

<style></style>
