<template>
  <div class="bg-slate-50 shadow">
    <div class="px-4 sm:px-6 lg:mx-auto lg:max-w-7xl lg:px-8">
      <div class="py-6 md:flex md:items-center md:justify-between">
        <div class="min-w-0 flex-1">
          <!-- Profile -->
          <div class="flex items-center">
            <img
              class="hidden h-16 w-16 rounded-full sm:block"
              src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.6&w=256&h=256&q=80"
              alt="" />
            <div>
              <div class="flex items-center">
                <img
                  class="h-16 w-16 rounded-full sm:hidden"
                  src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.6&w=256&h=256&q=80"
                  alt="" />
                <h1 class="ml-3 text-2xl font-bold leading-7 text-slate-900 sm:truncate sm:leading-9">
                  Good morning, {{ patientName }}
                </h1>
              </div>
              <dl class="mt-6 flex flex-col sm:ml-3 sm:mt-1 sm:flex-row sm:flex-wrap">
                <dt class="sr-only">Company</dt>
                <dd class="flex items-center text-sm font-medium capitalize text-slate-500 sm:mr-6">
                  <BuildingOfficeIcon class="mr-1.5 h-5 w-5 flex-shrink-0 text-slate-400" aria-hidden="true" />
                  {{ patientInsurance }}
                </dd>
                <dt class="sr-only">Account status</dt>
                <dd class="mt-3 flex items-center text-sm font-medium capitalize text-slate-500 sm:mr-6 sm:mt-0">
                  <CalendarDaysIcon class="mr-1.5 h-5 w-5 flex-shrink-0 text-slate-400" aria-hidden="true" />
                  {{ patientDob }}
                </dd>
              </dl>
            </div>
          </div>
        </div>
        <div class="mt-6 flex space-x-3 md:mt-0 md:ml-4">
          <button
            type="button"
            class="inline-flex items-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
            Edit Profile
          </button>
          <button
            type="button"
            class="inline-flex items-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
            Request Appointment
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { BuildingOfficeIcon, CalendarDaysIcon } from "@heroicons/vue/20/solid";

export default {
  props: ["patientName", "patientInsurance", "patientDob"],
};
</script>

<style></style>
