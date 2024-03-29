<template>
  <NuxtLayout :currentPage="thispage">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto">
          <h1 class="text-xl font-semibold text-gray-900">Your Medications</h1>
          <p class="mt-2 text-sm text-gray-700">A list of all the medications in your record.</p>
        </div>
        <div class="mt-4 sm:mt-0 sm:ml-16 sm:flex-none">
          <button
            type="button"
            class="inline-flex items-center justify-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 sm:w-auto">
            Add Medication
          </button>
        </div>
      </div>
      <div class="mt-8 flex flex-col">
        <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div class="inline-block min-w-full py-2 align-middle md:px-6 lg:px-8">
            <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5 md:rounded-lg">
              <table class="min-w-full divide-y divide-gray-300">
                <thead class="bg-gray-50">
                  <tr>
                    <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-6">
                      Name
                    </th>
                    <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Title</th>
                    <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-6">
                      <span class="sr-only">Edit</span>
                    </th>
                  </tr>
                </thead>
                <tbody class="divide-y divide-gray-200 bg-white">
                  <tr v-for="medication in medications" :key="medication.id">
                    <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm sm:pl-6">
                      <div class="font-medium text-gray-900">{{ medication.medication_name }}</div>
                    </td>
                    <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                      <span
                        class="inline-flex rounded-full bg-green-100 px-2 text-xs font-semibold leading-5 text-green-800"
                        >Active</span
                      >
                    </td>
                    <td>
                      <NuxtLink :to="'/medications' + '/' + medication.id">View Medication</NuxtLink>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
        <div>
          <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
          <div class="mt-1">
            <form @submit.prevent="addMedication">
              <input
                v-model="newMedication"
                name="newMedication"
                type="text"
                :loading="loading"
                class="block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm" />
              <button type="submit" variant="white">Add</button>
            </form>
          </div>
        </div>
        <NuxtPage :medication="medications" />
      </div>
    </div>
  </NuxtLayout>
</template>

<script setup>
const client = useSupabaseClient();

const route = useRoute();

const thispage = route.path;

const newMedication = ref("");
const loading = ref(null);

const { data: medications } = await useAsyncData("medications", async () => {
  const { data } = await client.from("medications").select();
  return data;
});

async function addMedication() {
  if (newMedication.value.trim().length === 0) {
    return;
  }
  loading.value = true;
  const { data } = await client
    .from("medications")
    .insert({
      medication_name: newMedication.value,
    })
    .select("id, medication_name")
    .single();
  medications.value.push(data);
  newMedication.value = "";
  loading.value = false;
}
</script>

<script>
export default {
  name: "Medications Home",
};
</script>

<style></style>
