<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> Quasar App </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Essential Links </q-item-label>

        <component-link
          v-for="link in componentLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';

import ComponentLink from '../components/ComponentLink.vue';
import { ComponentLinkProps } from '../components/ComponentLink.vue';

const componentLinks: ComponentLinkProps[] = [
  {
    title: 'Koleksiyon',
    caption: 'quasar.dev',
    icon: 'school',
    link: '/Koleksiyon',
  },
  {
    title: 'Ozellikler',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: '/Ozellikler',
  },
  {
    title: 'Blog',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: '/Blog',
  },
  {
    title: 'YeniUrunler',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: '/YeniUrunler',
  },
  
  {
    title: 'Cookies',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: '/Cookies',
  },
  
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
