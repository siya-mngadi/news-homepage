<template>
  <nav class="navbar navbar-expand-sm navbar-light bg-body-tertiary">
    <div class="container-fluid">
      <a class="navbar-brand" href="#home">
        <v-img :width="50" aspect-ratio="16/9" alt="logo" cover :src="appIcon" />
      </a>
      <button
        class="navbar-toggler shadow-none border-0"
        type="button"
        data-bs-toggle="offcanvas"
        data-bs-target="#navbarToggle"
        aria-controls="navbarToggle"
        aria-label="Toggle navigation"
      >
        <v-img :width="50" aspect-ratio="16/9" cover alt="menu icon" :src="menuIcon" />
      </button>

      <div
        class="offcanvas offcanvas-end"
        tabindex="-1"
        id="navbarToggle"
        aria-labelledby="navbarToggleLabel"
      >
        <div class="offcanvas-header">
          <v-btn
            type="button"
            class="btn-close"
            data-bs-dismiss="offcanvas"
            aria-label="Close"
            :elevation="0"
            :ripple="false"
          >
            <template #default>
              <v-img :width="35" aspect-ratio="auto" cover alt="close icon" :src="closeIcon" />
            </template>
          </v-btn>
        </div>

        <div class="offcanvas-body">
          <ul class="navbar-nav justify-content-end flex-grow-1 pe-3">
            <template v-for="link in navLinks" :key="link">
              <li class="nav-item mx-2" @click="() => handleClick(link)">
                <a
                  class="nav-link"
                  :aria-label="link"
                  :class="{ active: selectedLink === link }"
                  aria-current="page"
                  :href="`#${link?.toLowerCase()}`"
                >
                  {{ link }}
                </a>
              </li>
            </template>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import appIcon from '@/assets/images/logo.svg'
import closeIcon from '@/assets/images/icon-menu-close.svg'
import menuIcon from '@/assets/images/icon-menu.svg'
import { ref } from 'vue'

const navLinks = ['Home', 'New', 'Popular', 'Trending', 'Categories']
const selectedLink = ref(navLinks[0])

const handleClick = (navItem: string) => {
  selectedLink.value = navItem
}
</script>

<style lang="scss" scoped>
.navbar {
  background-color: white !important;
}

.navbar-toggler-icon {
  padding: 16px 20px !important;
}

.offcanvas.offcanvas-end {
  width: 70%;
}

a {
  font-weight: 500;
  color: var(--dark-grayish-blue);
}

.active {
  color: var(--red-soft) !important;
}
</style>
