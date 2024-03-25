<script setup lang="ts">
import AppLogo from 'src/components/AppLogo.vue';
import { ref } from 'vue';

const drawer = ref(true);
const miniDrawer = ref(true);
const onSearch = ref(false);
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
    <q-header bordered class="bg-white text-black">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="drawer = !drawer" />
        <q-toolbar-title>
          <AppLogo />
        </q-toolbar-title>
        <q-space />
        <q-input
          rounded
          outlined
          @focus="onSearch = true"
          @blur="onSearch = false"
        >
          <template v-slot:prepend>
            <q-icon v-if="onSearch" name="search" />
          </template>
          <template v-slot:append>
            <q-icon v-if="!onSearch" name="keyboard" />
            <q-btn rounded flat icon="search" />
          </template>
        </q-input>
        <q-btn round flat icon="mic" class="q-mx-md" />
        <q-space />
        <q-btn dense flat round icon="video_call" class="q-mx-md" />
        <q-btn dense flat round icon="notifications" class="q-mx-md">
          <q-badge color="red" rounded floating>+4</q-badge>
        </q-btn>
        <q-btn dense flat round class="q-mx-md">
          <q-avatar>
            <q-img src="https://cdn.quasar.dev/img/boy-avatar.png" />
          </q-avatar>
        </q-btn>
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
      <q-scroll-area class="fit" :horizontal-thumb-style="{ opacity: 0 }">
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
