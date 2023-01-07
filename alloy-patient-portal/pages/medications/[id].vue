<template>
  <div>Medication {{ $route.params.id }} {{ medications.medication_name }}</div>
</template>

<script setup>
const route = useRoute();
const id = route.params.id;

const client = useSupabaseClient();

const { data: medications } = await useAsyncData("medications", async () => {
  const { data } = await client.from("medications").select().single().match({ id: id });
  return data;
});
</script>

<script>
export default {
  name: "Medication Detail",
  props: {
    medication: {
      name: String,
      id: Number,
    },
  },
};
</script>

<style></style>
