<template>
  <NuxtLayout :currentPage="thispage">
    <template v-slot:header>
      <patient-header
        :patientName="patients.name"
        :patientInsurance="patients.insurance"
        :patientDob="patients.date_of_birth" />
    </template>
    Test
  </NuxtLayout>
</template>

<script setup>
import PatientHeader from "~/components/navigation/headers/PatientHeader.vue";
const route = useRoute();

const thispage = route.path;
const client = useSupabaseClient();

const { data: patients } = await useAsyncData("patients", async () => {
  const { data } = await client.from("patients").select("*").limit(1).single();
  return data;
});
</script>

<style></style>
