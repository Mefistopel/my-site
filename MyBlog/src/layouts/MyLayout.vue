<template>
  <q-layout view="lHh Lpr lFf">
    <q-layout-header>
      <q-toolbar
        color="purple-9"
        :glossy="$q.theme === 'mat'"
        :inverted="$q.theme === 'ios'"
      >
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
        >
          <q-icon name="menu" />
        </q-btn>
        <q-btn
          class="gt-md"
          flat
          label="Андрей Янусов"
          no-caps
          @click="$router.push('/')"
        />
      </q-toolbar>
      <!-- <q-toolbar-title>
          {{ timeData }}
      </q-toolbar-title> -->
    </q-layout-header>

    <q-layout-drawer
      v-model="leftDrawerOpen"
      :content-class="$q.theme === 'mat' ? 'black' : null"
      :content-style="{'background-color': '#6A1B9A'}"
    >
      <q-list
        no-border
        link
        inset-delimiter
        dark
      >
        <q-list-header>Страницы</q-list-header>
        <q-item to="about">
          <q-item-side icon="book" />
          <q-item-main label="Кто я" sublabel="Немного обо мне" />
        </q-item>
       <q-collapsible indent icon="school" label="Курсы" sublabel="Создаю курсы по известному">
        <q-collapsible label="Системный анализ">
          <q-item
          v-for="men in 5"
          :key="men"
          :to="'link'"
         >
          <q-item-main  :sublabel="men + ' Введение'" />
        </q-item>
        </q-collapsible>
      </q-collapsible>
        <q-item to="hi">
          <q-item-side icon="record_voice_over" />
          <q-item-main label="Знакомлюсь" sublabel="Познакомлюсь с девушкой ^_^" />
        </q-item>
        <q-item @click.native="openURL('https://vk.com/im?sel=44035224')">
          <q-item-side icon="send"  />
          <q-item-main label="Напиши мне в ВК!" sublabel="Давай, не стесняйся!" />
        </q-item>
        <q-item @click.native="openURL('https://www.instagram.com/an.yanusov/')">
          <q-item-side icon="check_box" />
          <q-item-main label="Instagramm" sublabel="@an.yanusov" />
        </q-item>
      </q-list>
    </q-layout-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop
    }
  },
  methods: {
    openURL,
    startCounting () {
      this.hndl = setInterval(() => {
        this.counter++
      }, 1000)
    }
  }
}
</script>

<style>
</style>
