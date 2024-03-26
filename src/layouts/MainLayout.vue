<script setup lang="ts">
import { useQuasar } from 'quasar';
import AppLogo from 'src/components/AppLogo.vue';
import SearchWrapper from 'src/components/SearchWrapper.vue';
import { ref } from 'vue';

const $q = useQuasar();
const drawer = ref(true);
const miniDrawer = ref(true);
const menus = ref([
  {
    name: 'home',
    label: 'Home',
  },
  {
    name: 'library_music',
    label: 'Shorts',
  },
  {
    name: 'subscriptions',
    label: 'Subscriptions',
  },
  {
    name: 'video_library',
    label: 'You',
  },
  {
    name: 'history',
    label: 'History',
  },
]);
</script>

<template>
  <q-layout view="hHh LpR lff" class="q-py-4">
    <q-header bordered class="bg-white text-black q-px-xs">
      <q-toolbar>
        <q-btn
          dense
          flat
          round
          icon="menu"
          :size="$q.screen.xs || $q.screen.sm ? 'sm' : 'md'"
          @click="drawer = !drawer"
        />
        <q-toolbar-title class="q-px-sm">
          <AppLogo />
        </q-toolbar-title>
        <q-space v-if="$q.screen.md" />
        <SearchWrapper />
        <q-space v-if="$q.screen.md" />
        <q-btn dense flat round icon="more_vert" class="q-mx-sm" />
        <q-btn
          outline
          rounded
          icon="account_circle"
          class="text-primary q-px-sm"
        >
          <span v-if="$q.screen.md" class="q-px-sm">Sign In</span>
        </q-btn>
        <q-btn dense flat round icon="invert_colors" class="q-mx-sm" />
      </q-toolbar>
    </q-header>

    <q-drawer
      show-if-above
      v-model="drawer"
      side="left"
      :mini="miniDrawer"
      @mouseout="miniDrawer = true"
      @mouseover="miniDrawer = false"
      :width="200"
      :breakpoint="500"
      bordered
    >
      <q-scroll-area class="fit" :horizontal-thumb-style="{ opacity: '0' }">
        <q-list padding>
          <q-item
            :key="menuIndex"
            v-for="(menu, menuIndex) in menus"
            clickable
            v-ripple
          >
            <q-item-section avatar>
              <q-icon :name="menu.name" />
            </q-item-section>

            <q-item-section>{{ menu.label }}</q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>
