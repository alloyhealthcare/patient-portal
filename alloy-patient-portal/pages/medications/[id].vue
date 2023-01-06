<template>
  <div>Medication {{ medications.medication_name }}</div>
</template>

<script setup>
const route = useRoute();
const id = route.params.id;

const client = useSupabaseClient();

const { data: medications } = await useAsyncData("medications", async () => {
  const { data } = await client.from("medications").select().match({ id: id }).single();
  return data;
});
</script>

<script>
export default {
  name: "Medication Detail",
};
</script>

<style></style>
