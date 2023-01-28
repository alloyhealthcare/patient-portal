<template>
  <div>
    <NuxtLayout :currentPage="thispage">
      <template v-slot:header>
        <patient-header
          :patientName="patients.name"
          :patientInsurance="patients.insurance"
          :patientDob="patients.date_of_birth" />
      </template>
      <div class="mb-6">
        <h2 class="text-lg font-medium leading-6 text-slate-900">Overview</h2>
        <div class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3">
          <!-- Card -->

          <div v-for="card in cards" :key="card.name" class="overflow-hidden rounded-lg bg-white shadow">
            <div class="p-5">
              <div class="flex items-center">
                <div class="w-0 flex-1">
                  <dl>
                    <dt class="truncate text-sm font-medium text-slate-500">{{ card.name }}</dt>
                    <dd>
                      <div class="text-lg font-medium text-slate-900">{{ card.amount }}</div>
                    </dd>
                  </dl>
                </div>
              </div>
            </div>
            <div class="bg-slate-50 px-5 py-3">
              <div class="text-sm">
                <a :href="card.href" class="font-medium text-indigo-700 hover:text-indigo-900">{{ card.action }}</a>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="grid grid-cols-3 gap-x-4 pt-12">
        <section aria-labelledby="quick-links-title" class="col-span-2">
          <h2 class="text-lg font-medium leading-6 text-slate-900 mb-4">Manage Your Care</h2>
          <div
            class="divide-y divide-slate-200 overflow-hidden rounded-lg bg-slate-200 shadow sm:grid sm:grid-cols-2 sm:gap-px sm:divide-y-0">
            <h2 class="sr-only" id="quick-links-title">Quick links</h2>
            <div
              v-for="(action, actionIdx) in actions"
              :key="action.name"
              :class="[
                actionIdx === 0 ? 'rounded-tl-lg rounded-tr-lg sm:rounded-tr-none' : '',
                actionIdx === 1 ? 'sm:rounded-tr-lg' : '',
                actionIdx === actions.length - 2 ? 'sm:rounded-bl-lg' : '',
                actionIdx === actions.length - 1 ? 'rounded-bl-lg rounded-br-lg sm:rounded-bl-none' : '',
                'relative group bg-white p-6 focus-within:ring-2 focus-within:ring-inset focus-within:ring-cyan-500',
              ]">
              <div>
                <span
                  :class="[
                    action.iconBackground,
                    action.iconForeground,
                    'rounded-lg inline-flex p-3 ring-4 ring-white',
                  ]">
                  <component :is="action.icon" class="h-6 w-6" aria-hidden="true" />
                </span>
              </div>
              <div class="mt-8">
                <h3 class="text-lg font-medium">
                  <a :href="action.href" class="focus:outline-none">
                    <!-- Extend touch target to entire panel -->
                    <span class="absolute inset-0" aria-hidden="true" />
                    {{ action.name }}
                  </a>
                </h3>
                <p class="mt-2 text-sm text-slate-500">
                  Doloribus dolores nostrum quia qui natus officia quod et dolorem. Sit repellendus qui ut at blanditiis
                  et quo et molestiae.
                </p>
              </div>
              <span
                class="pointer-events-none absolute top-6 right-6 text-slate-300 group-hover:text-slate-400"
                aria-hidden="true">
                <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M20 4h1a1 1 0 00-1-1v1zm-1 12a1 1 0 102 0h-2zM8 3a1 1 0 000 2V3zM3.293 19.293a1 1 0 101.414 1.414l-1.414-1.414zM19 4v12h2V4h-2zm1-1H8v2h12V3zm-.707.293l-16 16 1.414 1.414 16-16-1.414-1.414z" />
                </svg>
              </span>
            </div>
          </div>
        </section>
        <div class="col-span-1">
          <h2 class="text-lg font-medium leading-6 text-slate-900 mb-4">Comming Up</h2>
          <div class="overflow-hidden bg-white shadow sm:rounded-md">
            <ul role="list" class="divide-y divide-slate-200">
              <li v-for="position in positions" :key="position.id">
                <a href="#" class="block hover:bg-slate-50">
                  <div class="px-4 py-4 sm:px-6 flex flex-row items-center justify-between">
                    <div class="flex items-center justify-between">
                      <p class="truncate text-sm font-medium text-indigo-600">{{ position.title }}</p>
                    </div>
                    <div class="mt-2 sm:flex sm:justify-between">
                      <div class="flex items-center text-sm text-slate-500 sm:mt-0">
                        <CalendarIcon class="mr-1.5 h-5 w-5 flex-shrink-0 text-slate-400" aria-hidden="true" />
                        <p>
                          <time :datetime="position.closeDateFull">{{ position.closeDateFull }}</time>
                        </p>
                      </div>
                    </div>
                  </div>
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </NuxtLayout>
  </div>
</template>

<script setup lang="ts">
import {
  ClockIcon,
  AcademicCapIcon,
  BanknotesIcon,
  CheckBadgeIcon,
  ReceiptRefundIcon,
  UsersIcon,
  ChartBarIcon,
  ChatBubbleBottomCenterIcon,
  ChatBubbleLeftEllipsisIcon,
  DocumentCheckIcon,
} from "@heroicons/vue/24/outline";

import PatientHeader from "~/components/navigation/headers/PatientHeader.vue";

import { CalendarIcon } from "@heroicons/vue/24/solid";

const route = useRoute();

const thispage = route.path;

const client = useSupabaseClient();

const { data: patients } = await useAsyncData("patients", async () => {
  const { data } = await client.from("patients").select("*").limit(1).single();
  return data;
});

const cards = [
  { name: "Overdue", href: "#", amount: "Hepatitis B Vaccine", action: "View All Overdue" },
  { name: "Primary Care Physician", href: "#", amount: "John K. Watson MD", action: "See All Care Team" },
  { name: "Results", href: "#", amount: "Comprehensive Metabolic Panel", action: "View Results" },
];

const positions = [
  {
    id: 1,
    title: "Annual Physical",
    closeDateFull: "January 7, 2020",
  },
  {
    id: 2,
    title: "Refill Lisinopril",
    closeDateFull: "January 15, 2020",
  },
];
const actions = [
  {
    icon: UsersIcon,
    name: "View Care Team",
    href: "#",
    iconForeground: "text-teal-700",
    iconBackground: "bg-teal-50",
  },
  {
    icon: ChatBubbleLeftEllipsisIcon,
    name: "Ask a Question",
    href: "#",
    iconForeground: "text-purple-700",
    iconBackground: "bg-purple-50",
  },
  {
    icon: ChartBarIcon,
    name: "Track My Health",
    href: "#",
    iconForeground: "text-sky-700",
    iconBackground: "bg-sky-50",
  },
  {
    icon: BanknotesIcon,
    name: "Coverage Details",
    href: "#",
    iconForeground: "text-yellow-700",
    iconBackground: "bg-yellow-50",
  },
  {
    icon: DocumentCheckIcon,
    name: "Health Summary",
    href: "#",
    iconForeground: "text-rose-700",
    iconBackground: "bg-rose-50",
  },
  {
    icon: AcademicCapIcon,
    name: "Learning Library",
    href: "#",
    iconForeground: "text-indigo-700",
    iconBackground: "bg-indigo-50",
  },
];
</script>

<style></style>
