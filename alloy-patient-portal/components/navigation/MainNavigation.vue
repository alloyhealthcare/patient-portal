<template>
  <Disclosure as="nav" class="bg-white border-b border-slate-200 shadow" v-slot="{ open }">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="flex h-16 justify-between">
        <div class="flex">
          <div class="-ml-2 mr-2 flex items-center md:hidden">
            <!-- Mobile menu button -->
            <DisclosureButton
              class="inline-flex items-center justify-center rounded-md p-2 text-slate-400 hover:bg-slate-100 hover:text-slate-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500">
              <span class="sr-only">Open main menu</span>
              <Bars3Icon v-if="!open" class="block h-6 w-6" aria-hidden="true" />
              <XMarkIcon v-else class="block h-6 w-6" aria-hidden="true" />
            </DisclosureButton>
          </div>
          <div class="flex flex-shrink-0 items-center">
            <a href="/">
              <svg width="auto" height="16" viewBox="0 0 447 144" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0 140V0H45V50H90V0H135V140H90V90H45V140H0Z" fill="#00152F" />
                <path
                  d="M157.984 83V0H202.984V81C202.984 88.0667 204.984 93.6667 208.984 97.8C213.118 101.933 218.451 104 224.984 104C231.518 104 236.784 101.933 240.784 97.8C244.918 93.5333 246.984 87.9333 246.984 81V0H291.984V82.8C291.984 101.333 286.051 116.2 274.184 127.4C262.318 138.467 245.918 144 224.984 144C204.184 144 187.784 138.467 175.784 127.4C163.918 116.333 157.984 101.533 157.984 83Z"
                  fill="#00152F" />
                <path
                  d="M315.039 140V0H394.039C408.839 0 420.372 3.26667 428.639 9.8C436.906 16.3333 441.039 24.4 441.039 34C441.039 43.3333 437.172 51.0667 429.439 57.2C426.372 59.6 422.572 61.5333 418.039 63V65.2C423.106 66.4 427.772 68.4 432.039 71.2C441.372 77.6 446.039 86.8667 446.039 99C446.039 111 441.372 120.867 432.039 128.6C422.706 136.2 409.372 140 392.039 140H315.039ZM360.039 53H382.039C390.039 53 394.039 49.6667 394.039 43C394.039 36.3333 390.039 33 382.039 33H360.039V53ZM360.039 107H385.039C389.972 107 393.706 105.933 396.239 103.8C398.772 101.533 400.039 98.6 400.039 95C400.039 91.4 398.772 88.5333 396.239 86.4C393.706 84.1333 389.972 83 385.039 83H360.039V107Z"
                  fill="#00152F" />
              </svg>
            </a>
          </div>
          <div class="hidden md:ml-6 md:flex md:space-x-8">
            <!-- Current: "border-indigo-500 text-slate-900", Default: "border-transparent text-slate-500 hover:border-slate-300 hover:text-slate-700" -->
            <NuxtLink
              v-for="page in pages"
              :to="page.href"
              :class="{ 'border-indigo-500 border-b-2  text-slate-900': currentPage === pages.href }"
              class="inline-flex items-center border-b-2 px-1 pt-1 border-transparent text-sm font-medium text-slate-500 hover:border-slate-300 hover:text-slate-700"
              >{{ page.name }}</NuxtLink
            >
            <Menu as="div" class="relative h-full">
              <div class="h-full">
                <MenuButton
                  class="flex h-full items-center space-x-2 bg-white text-sm font-medium border-b-2 border-transparent pt-1 text-slate-500 hover:border-slate-300 hover:text-slate-700">
                  <span class="sr-only">Open user menu</span>
                  <span class="text-sm font-medium text-slate-500">More</span>
                  <EllipsisHorizontalIcon class="-ml-1 mr-2 h-5 w-5" aria-hidden="true" />
                </MenuButton>
              </div>
              <transition
                enter-active-class="transition ease-out duration-200"
                enter-from-class="transform opacity-0 scale-95"
                enter-to-class="transform opacity-100 scale-100"
                leave-active-class="transition ease-in duration-75"
                leave-from-class="transform opacity-100 scale-100"
                leave-to-class="transform opacity-0 scale-95">
                <MenuItems
                  class="absolute divide-y divide-slate-100 left-0 z-10 mt-2 w-48 origin-top-right rounded-md bg-white py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none">
                  <div>
                    <div class="text-xs font-semibold uppercase px-4 pt-2 pb-1 text-slate-500">Find Care</div>
                    <MenuItem v-slot="{ active }">
                      <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                        >Care Team</a
                      >
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                        >Search for a Clinician</a
                      >
                    </MenuItem>
                  </div>
                  <div>
                    <MenuItem v-slot="{ active }">
                      <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                        >Health Summary</a
                      >
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                        >Plan of Care</a
                      >
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                        >Medical History</a
                      >
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                        >Family History</a
                      >
                    </MenuItem>
                  </div>
                  <div>
                    <MenuItem v-slot="{ active }">
                      <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                        >Insurance Summary</a
                      >
                    </MenuItem>
                  </div>
                </MenuItems>
              </transition>
            </Menu>
          </div>
        </div>
        <div class="flex items-center">
          <div class="flex-shrink-0">
            <!--<button
              type="button"
              class="relative inline-flex items-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
              <PlusIcon class="-ml-1 mr-2 h-5 w-5" aria-hidden="true" />
              <span>Request Appointment</span>
            </button>-->
          </div>
          <div class="hidden md:ml-4 md:flex md:flex-shrink-0 md:items-center">
            <button
              type="button"
              class="rounded-full bg-white p-1 text-slate-400 hover:text-slate-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
              <span class="sr-only">View notifications</span>
              <BellIcon class="h-6 w-6" aria-hidden="true" />
            </button>

            <!-- Profile dropdown -->
            <Menu as="div" class="relative ml-3">
              <div>
                <MenuButton
                  class="flex rounded-full bg-white text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
                  <span class="sr-only">Open user menu</span>
                  <img
                    class="h-8 w-8 rounded-full"
                    src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.6&w=256&h=256&q=80"
                    alt="" />
                </MenuButton>
              </div>
              <transition
                enter-active-class="transition ease-out duration-200"
                enter-from-class="transform opacity-0 scale-95"
                enter-to-class="transform opacity-100 scale-100"
                leave-active-class="transition ease-in duration-75"
                leave-from-class="transform opacity-100 scale-100"
                leave-to-class="transform opacity-0 scale-95">
                <MenuItems
                  class="absolute right-0 z-10 mt-2 w-48 origin-top-right rounded-md bg-white py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none">
                  <MenuItem v-slot="{ active }">
                    <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                      >Your Profile</a
                    >
                  </MenuItem>
                  <MenuItem v-slot="{ active }">
                    <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                      >Settings</a
                    >
                  </MenuItem>
                  <MenuItem v-slot="{ active }">
                    <a href="#" :class="[active ? 'bg-slate-100' : '', 'block px-4 py-2 text-sm text-slate-700']"
                      >Sign out</a
                    >
                  </MenuItem>
                </MenuItems>
              </transition>
            </Menu>
          </div>
        </div>
      </div>
    </div>

    <DisclosurePanel class="md:hidden">
      <div class="space-y-1 pt-2 pb-3">
        <!-- Current: "bg-indigo-50 border-indigo-500 text-indigo-700", Default: "border-transparent text-slate-500 hover:bg-slate-50 hover:border-slate-300 hover:text-slate-700" -->
        <DisclosureButton
          as="a"
          href="#"
          class="block border-l-4 border-indigo-500 bg-indigo-50 py-2 pl-3 pr-4 text-base font-medium text-indigo-700 sm:pl-5 sm:pr-6"
          >Dashboard</DisclosureButton
        >
        <DisclosureButton
          as="a"
          href="#"
          class="block border-l-4 border-transparent py-2 pl-3 pr-4 text-base font-medium text-slate-500 hover:border-slate-300 hover:bg-slate-50 hover:text-slate-700 sm:pl-5 sm:pr-6"
          >Team</DisclosureButton
        >
        <DisclosureButton
          as="a"
          href="#"
          class="block border-l-4 border-transparent py-2 pl-3 pr-4 text-base font-medium text-slate-500 hover:border-slate-300 hover:bg-slate-50 hover:text-slate-700 sm:pl-5 sm:pr-6"
          >Projects</DisclosureButton
        >
        <DisclosureButton
          as="a"
          href="#"
          class="block border-l-4 border-transparent py-2 pl-3 pr-4 text-base font-medium text-slate-500 hover:border-slate-300 hover:bg-slate-50 hover:text-slate-700 sm:pl-5 sm:pr-6"
          >Calendar</DisclosureButton
        >
      </div>
      <div class="border-t border-slate-200 pt-4 pb-3">
        <div class="flex items-center px-4 sm:px-6">
          <div class="flex-shrink-0">
            <img
              class="h-10 w-10 rounded-full"
              src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.6&w=256&h=256&q=80"
              alt="" />
          </div>
          <div class="ml-3">
            <div class="text-base font-medium text-slate-800">Tom Cook</div>
            <div class="text-sm font-medium text-slate-500">tom@example.com</div>
          </div>
          <button
            type="button"
            class="ml-auto flex-shrink-0 rounded-full bg-white p-1 text-slate-400 hover:text-slate-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
            <span class="sr-only">View notifications</span>
            <BellIcon class="h-6 w-6" aria-hidden="true" />
          </button>
        </div>
        <div class="mt-3 space-y-1">
          <DisclosureButton
            as="a"
            href="#"
            class="block px-4 py-2 text-base font-medium text-slate-500 hover:bg-slate-100 hover:text-slate-800 sm:px-6"
            >Your Profile</DisclosureButton
          >
          <DisclosureButton
            as="a"
            href="#"
            class="block px-4 py-2 text-base font-medium text-slate-500 hover:bg-slate-100 hover:text-slate-800 sm:px-6"
            >Settings</DisclosureButton
          >
          <DisclosureButton
            as="a"
            href="#"
            class="block px-4 py-2 text-base font-medium text-slate-500 hover:bg-slate-100 hover:text-slate-800 sm:px-6"
            >Sign out</DisclosureButton
          >
        </div>
      </div>
    </DisclosurePanel>
  </Disclosure>
</template>

<script>
export default {
  name: "Main Navigation",
};
</script>

<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel, Menu, MenuButton, MenuItem, MenuItems } from "@headlessui/vue";
import { Bars3Icon, BellIcon, XMarkIcon } from "@heroicons/vue/24/outline";
import { PlusIcon, EllipsisHorizontalIcon } from "@heroicons/vue/20/solid";

const pages = [
  { name: "Dashboard", href: "/" },
  { name: "Visits", href: "/visits" },
  { name: "Messages", href: "/messages" },
  { name: "Medications", href: "/medications" },
];

const props = defineProps({
  currentPage: {
    type: String,
    required: true,
  },
});

// const isActive = this.route.params.path === pages.href;
</script>
