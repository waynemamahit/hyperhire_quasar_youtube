<script setup lang="ts">
const items: {
  title: string;
  channel: string;
  caption: string;
  views: number;
  image: string;
  avatar: string;
}[] = [
  {
    title: 'Parallax 1',
    channel: 'Lorem ipsum, sdfasjdfakldjsfklajsdf',
    caption: '1 hour ago',
    views: 40,
    image: 'https://cdn.quasar.dev/img/parallax1.jpg',
    avatar: 'https://cdn.quasar.dev/img/avatar2.jpg',
  },
  {
    title: 'Parallax 2',
    channel: 'Lorem ipsum, sdfasjdfakldjsfklajsdf',
    caption: '2 day ago',
    views: 30,
    image: 'https://cdn.quasar.dev/img/parallax2.jpg',
    avatar: 'https://cdn.quasar.dev/img/avatar1.jpg',
  },
  {
    title: 'Mountains',
    channel: 'Lorem ipsum, sdfasjdfakldjsfklajsdf',
    caption: '3 month ago',
    views: 20,
    image: 'https://cdn.quasar.dev/img/mountains.jpg',
    avatar: 'https://cdn.quasar.dev/img/avatar2.jpg',
  },
  {
    title: 'Quasar',
    channel: 'Lorem ipsum, sdfasjdfakldjsfklajsdf',
    caption: '4 year ago',
    views: 10,
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
              <q-item-label>{{ data.channel }}</q-item-label>
              <q-item-label caption
                >{{ data.caption }} - {{ data.views }} views</q-item-label
              >
            </q-item-section>
          </q-item>
        </q-card>
      </div>
    </div>
  </q-page>
</template>
