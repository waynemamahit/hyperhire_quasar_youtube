<script setup lang="ts">
const items: {
  title: string;
  author: string;
  caption: string;
  image: string;
}[] = [
  {
    title: 'Parallax 1',
    subtitle: 'Lorem ipsum, sdfasjdfakldjsfklajsdf',
    caption: '1 hour ago',
    image: 'https://cdn.quasar.dev/img/parallax1.jpg',
    avatar: 'https://cdn.quasar.dev/img/avatar2.jpg',
  },
  {
    title: 'Parallax 2',
    author: 'Lorem ipsum, sdfasjdfakldjsfklajsdf',
    caption: '2 day ago',
    image: 'https://cdn.quasar.dev/img/parallax2.jpg',
    avatar: 'https://cdn.quasar.dev/img/avatar1.jpg',
  },
  {
    title: 'Mountains',
    author: 'Lorem ipsum, sdfasjdfakldjsfklajsdf',
    caption: '3 month ago',
    image: 'https://cdn.quasar.dev/img/mountains.jpg',
    avatar: 'https://cdn.quasar.dev/img/avatar2.jpg',
  },
  {
    title: 'Quasar',
    author: 'Lorem ipsum, sdfasjdfakldjsfklajsdf',
    caption: '4 year ago',
    image: 'https://cdn.quasar.dev/img/quasar.jpg',
    avatar: 'https://cdn.quasar.dev/img/avatar1.jpg',
  },
];
</script>

<template>
  <q-page class="q-pa-md">
    <div class="row justify-around">
      <div
        v-for="(data, index) in items"
        :key="index"
        class="q-col-lg-3 q-col-md-4"
      >
        <q-card style="width: 310px" flat>
          <q-img :src="data.image" height="220px" />
          <q-item>
            <q-item-section avatar>
              <q-avatar>
                <q-img :src="data.avatar" />
              </q-avatar>
            </q-item-section>

            <q-item-section>
              <q-item-label>{{ data.title }}</q-item-label>
              <q-item-label caption>{{ data.author }}</q-item-label>
              <q-item-label caption>{{ data.caption }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-card>
      </div>
    </div>
  </q-page>
</template>
