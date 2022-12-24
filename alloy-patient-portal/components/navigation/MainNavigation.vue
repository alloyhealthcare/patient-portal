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
              <svg width="auto" height="16" viewBox="0 0 980 148" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M467.6 127.2C453.867 113.2 447 95.4667 447 74C447 52.5333 453.867 34.8667 467.6 21C481.467 7 498.933 0 520 0C543.6 0 562.2 8.53333 575.8 25.6C581.8 32.9333 586.2 41.4 589 51H571C568.2 44.3333 564.667 38.6667 560.4 34C549.867 22.6667 536.4 17 520 17C503.867 17 490.667 22.2667 480.4 32.8C470.133 43.3333 465 57.0667 465 74C465 90.9333 470.133 104.667 480.4 115.2C490.667 125.733 503.867 131 520 131C536.667 131 550.467 124.867 561.4 112.6C565.8 107.533 569.333 101.333 572 94H590C586.8 104.4 582.133 113.4 576 121C562 139 543.333 148 520 148C498.933 148 481.467 141.067 467.6 127.2ZM611.961 4H627.961V59H628.161C630.161 55.8 632.761 53 635.961 50.6C643.294 44.8667 651.961 42 661.961 42C674.094 42 683.761 45.8667 690.961 53.6C698.294 61.2 701.961 71.6667 701.961 85V144H685.961V86C685.961 76.4 683.561 69.2 678.761 64.4C673.961 59.4667 667.361 57 658.961 57C649.761 57 642.294 60.0667 636.561 66.2C630.828 72.2 627.961 80.1333 627.961 90V144H611.961V4ZM721.977 94C721.977 108.8 726.643 121.2 735.977 131.2C745.31 141.067 756.643 146 769.977 146C778.51 146 785.71 144.4 791.577 141.2C797.443 137.867 801.577 134.4 803.977 130.8L805.777 128H805.977V144H821.977V44H805.977V60.2H805.777L803.977 57.2C801.31 53.4667 797.043 50 791.177 46.8C785.443 43.6 778.377 42 769.977 42C756.643 42 745.31 47 735.977 57C726.643 66.8667 721.977 79.2 721.977 94ZM737.977 94C737.977 83.2 741.177 74.3333 747.577 67.4C754.11 60.4667 762.243 57 771.977 57C781.71 57 789.777 60.4667 796.177 67.4C802.71 74.3333 805.977 83.2 805.977 94C805.977 104.8 802.71 113.667 796.177 120.6C789.777 127.533 781.71 131 771.977 131C762.243 131 754.11 127.533 747.577 120.6C741.177 113.667 737.977 104.8 737.977 94ZM850.047 144V44H866.047V60H866.247C868.114 56.6667 870.38 53.8667 873.047 51.6C879.58 45.8667 887.58 43 897.047 43H909.047V59H897.047C887.98 59 880.514 61.9333 874.647 67.8C868.914 73.5333 866.047 80.9333 866.047 90V144H850.047ZM917.023 44V59H930.023V144H979.023V129H946.023V59H978.023V44H946.023V22H930.023V44H917.023ZM0 4V144H28V90C28 82.1333 30.3333 75.6667 35 70.6C39.6667 65.5333 45.3333 63 52 63C58.6667 63 63.8 65 67.4 69C71.1333 72.8667 73 78.5333 73 86V144H101V82C101 68 97.4667 57.3333 90.4 50C83.4667 42.6667 73.6667 39 61 39C51.9333 39 43.7333 41.8667 36.4 47.6C33.2 50.1333 30.7333 52.9333 29 56H28V4H0ZM116.07 93C116.07 108.067 121.337 120.867 131.87 131.4C142.537 141.8 155.604 147 171.07 147C189.07 147 203.404 141 214.07 129C218.47 123.8 221.804 117.8 224.07 111H194.07C192.87 113.267 191.27 115.267 189.27 117C184.204 121 178.137 123 171.07 123C164.67 123 159.004 120.667 154.07 116C149.137 111.333 146.137 105.667 145.07 99H225.07V93C225.07 77.8 220.004 65 209.87 54.6C199.737 44.2 186.804 39 171.07 39C155.604 39 142.537 44.2667 131.87 54.8C121.337 65.2 116.07 77.9333 116.07 93ZM195.07 82H146.07C147.67 76.5333 150.67 72 155.07 68.4C159.47 64.8 164.804 63 171.07 63C177.337 63 182.604 64.8667 186.87 68.6C191.27 72.2 194.004 76.6667 195.07 82ZM241.992 144V42H269.992V57H270.992C272.192 53.8 273.992 51 276.392 48.6C281.859 42.8667 288.726 40 296.992 40H308.992V67H293.992C286.392 67 280.459 69.0667 276.192 73.2C272.059 77.2 269.992 82.8 269.992 90V144H241.992ZM317.047 93C317.047 108.067 322.38 120.867 333.047 131.4C343.714 141.8 357.047 147 373.047 147C388.914 147 402.18 141.8 412.847 131.4C423.647 120.867 429.047 108.067 429.047 93C429.047 77.9333 423.647 65.2 412.847 54.8C402.18 44.2667 388.914 39 373.047 39C357.047 39 343.714 44.2667 333.047 54.8C322.38 65.2 317.047 77.9333 317.047 93ZM346.047 93C346.047 84.2 348.647 77 353.847 71.4C359.047 65.8 365.447 63 373.047 63C380.647 63 387.047 65.8 392.247 71.4C397.447 77 400.047 84.2 400.047 93C400.047 101.8 397.447 109 392.247 114.6C387.047 120.2 380.647 123 373.047 123C365.447 123 359.047 120.2 353.847 114.6C348.647 109 346.047 101.8 346.047 93Z"
                  fill="#00152F" />
              </svg>
            </a>
          </div>
          <div class="hidden md:ml-6 md:flex md:space-x-8">
            <!-- Current: "border-indigo-500 text-slate-900", Default: "border-transparent text-slate-500 hover:border-slate-300 hover:text-slate-700" -->
            <NuxtLink
              to="/"
              class="inline-flex items-center border-b-2 border-transparent hover:border-slate-300 hover:text-slate-700 text-slate-500 px-1 pt-1 text-sm font-medium"
              exact-active-class="border-indigo-500 border-b-2 text-slate-900"
              >Dashboard</NuxtLink
            >
            <NuxtLink
              to="/visits"
              class="inline-flex items-center border-b-2 border-transparent px-1 pt-1 text-sm font-medium text-slate-500 hover:border-slate-300 hover:text-slate-700"
              exact-active-class="border-indigo-500 border-b-2 text-slate-900"
              >Visits</NuxtLink
            >
            <NuxtLink
              to="/medications"
              class="inline-flex items-center border-b-2 border-transparent px-1 pt-1 text-sm font-medium text-slate-500 hover:border-slate-300 hover:text-slate-700"
              activeClass="border-indigo-500 text-slate-900"
              >Medications</NuxtLink
            >
            <NuxtLink
              to="/messages"
              class="inline-flex items-center border-b-2 border-transparent px-1 pt-1 text-sm font-medium text-slate-500 hover:border-slate-300 hover:text-slate-700"
              active-class="border-indigo-500 text-slate-900"
              >Messages</NuxtLink
            >
            <Menu as="div" class="relative self-center">
              <div>
                <MenuButton
                  class="flex rounded-full space-x-2 bg-white text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
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
                    src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
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

<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel, Menu, MenuButton, MenuItem, MenuItems } from "@headlessui/vue";
import { Bars3Icon, BellIcon, XMarkIcon } from "@heroicons/vue/24/outline";
import { PlusIcon, EllipsisHorizontalIcon } from "@heroicons/vue/20/solid";
</script>
