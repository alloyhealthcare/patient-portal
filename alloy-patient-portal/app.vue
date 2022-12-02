<template>
  <div>
    <NuxtLayout>
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
                      Good morning, Emilia Birch
                    </h1>
                  </div>
                  <dl class="mt-6 flex flex-col sm:ml-3 sm:mt-1 sm:flex-row sm:flex-wrap">
                    <dt class="sr-only">Company</dt>
                    <dd class="flex items-center text-sm font-medium capitalize text-slate-500 sm:mr-6">
                      <BuildingOfficeIcon class="mr-1.5 h-5 w-5 flex-shrink-0 text-slate-400" aria-hidden="true" />
                      Blue Cross PPO
                    </dd>
                    <dt class="sr-only">Account status</dt>
                    <dd class="mt-3 flex items-center text-sm font-medium capitalize text-slate-500 sm:mr-6 sm:mt-0">
                      <CheckCircleIcon class="mr-1.5 h-5 w-5 flex-shrink-0 text-green-400" aria-hidden="true" />
                      February 03, 1986
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

      <div class="py-8">
        <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
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
        </div>
      </div>
      <div class="py-12">
        <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
          <div class="grid grid-cols-3 gap-x-4">
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
                      Doloribus dolores nostrum quia qui natus officia quod et dolorem. Sit repellendus qui ut at
                      blanditiis et quo et molestiae.
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
                      <div class="px-4 py-4 sm:px-6">
                        <div class="flex items-center justify-between">
                          <p class="truncate text-sm font-medium text-indigo-600">{{ position.title }}</p>
                        </div>
                        <div class="mt-2 sm:flex sm:justify-between">
                          <div class="sm:flex"></div>
                          <div class="mt-2 flex items-center text-sm text-slate-500 sm:mt-0">
                            <CalendarIcon class="mr-1.5 h-5 w-5 flex-shrink-0 text-slate-400" aria-hidden="true" />
                            <p>
                              Closing on
                              {{ " " }}
                              <time :datetime="position.closeDate">{{ position.closeDateFull }}</time>
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
        </div>
      </div>
    </NuxtLayout>
  </div>
</template>

<script setup>
import { ref } from "vue";
import {
  Dialog,
  DialogPanel,
  Menu,
  MenuButton,
  MenuItem,
  MenuItems,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import {
  Bars3CenterLeftIcon,
  BellIcon,
  ClockIcon,
  CogIcon,
  CreditCardIcon,
  DocumentChartBarIcon,
  HomeIcon,
  QuestionMarkCircleIcon,
  ScaleIcon,
  ShieldCheckIcon,
  UserGroupIcon,
  XMarkIcon,
  AcademicCapIcon,
  BanknotesIcon,
  Bars3Icon,
  CheckBadgeIcon,
  ReceiptRefundIcon,
  UsersIcon,
} from "@heroicons/vue/24/outline";
import {
  BuildingOfficeIcon,
  CheckCircleIcon,
  ChevronDownIcon,
  ChevronRightIcon,
  MagnifyingGlassIcon,
} from "@heroicons/vue/20/solid";

const cards = [
  { name: "Overdue", href: "#", amount: "Hepatitis B Vaccine", action: "View All Overdue" },
  { name: "Primary Care Physician", href: "#", amount: "John K. Watson MD", action: "See All Care Team" },
  { name: "Results", href: "#", amount: "Comprehensive Metabolic Panel", action: "View Results" },
  // More items...
];
const positions = [
  {
    id: 1,
    title: "Back End Developer",
    type: "Full-time",
    location: "Remote",
    department: "Engineering",
    closeDate: "2020-01-07",
    closeDateFull: "January 7, 2020",
  },
  {
    id: 2,
    title: "Front End Developer",
    type: "Full-time",
    location: "Remote",
    department: "Engineering",
    closeDate: "2020-01-07",
    closeDateFull: "January 7, 2020",
  },
  {
    id: 3,
    title: "User Interface Designer",
    type: "Full-time",
    location: "Remote",
    department: "Design",
    closeDate: "2020-01-14",
    closeDateFull: "January 14, 2020",
  },
];
const actions = [
  {
    icon: ClockIcon,
    name: "View Care Team",
    href: "#",
    iconForeground: "text-teal-700",
    iconBackground: "bg-teal-50",
  },
  {
    icon: CheckBadgeIcon,
    name: "Ask a Question",
    href: "#",
    iconForeground: "text-purple-700",
    iconBackground: "bg-purple-50",
  },
  {
    icon: UsersIcon,
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
    icon: ReceiptRefundIcon,
    name: "Submit an expense",
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
