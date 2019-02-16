<template>
  <q-page class="flex ">
    <q-card
      dark
      class="q-ma-md"
      text-color="grey-3"
      inline style="width: 900px"
      :style="{'background-color': '#6A1B9A'}" >
      <q-card-title>
        {{ title }}
        <span slot="subtitle">Янусов Андрей Сергеевич</span>
      <div slot="right" class="row items-center">
        <q-icon slot="right" name="more_vert">
          <q-popover>
            <q-list
              dark
              :style="{'background-color': '#6A1B9A'}"
              link
              class="no-border">
              <q-item
                v-for="type in types"
                :key="type.title"
                @click.native="type.handler()"
                v-close-overlay>
                <q-item-main :label="type.label" />
              </q-item>
            </q-list>
          </q-popover>
        </q-icon>
      </div>
    </q-card-title>
    <q-card-separator />
     <q-card-main>
        <app-education v-if="title == 'Образование'"></app-education>
        {{ lorem }}
      </q-card-main>
    </q-card>
  </q-page>
</template>

<style>
</style>

<script>
import Education from '../components/education.vue'

export default {
  name: 'PageIndex',
  components: {
    appEducation: Education
  },
  data () {
    return {
      types: [
        {
          label: 'Образование',
          handler: () => {
            this.education()
          }
        },
        {
          label: 'Карьера',
          handler: () => {
            this.work()
          }
        },
        {
          label: 'Достижения',
          handler: () => {
            this.trackRecord()
          }
        },
        {
          label: 'Навыки, знания',
          handler: () => {
            this.skills()
          }
        },
        {
          label: 'Личные качества',
          handler: () => {
            this.personalQuality(true)
          }
        },
        {
          label: 'Интересы, хобби',
          handler: () => {
            this.hobby()
          }
        }
      ],
      title: 'Категория',
      lorem: 'Выбери то, что хочешь узнать'
    }
  },
  methods: {
    education () {
      this.title = 'Образование'
      this.lorem = 'Blead'
    }
  }
}
</script>
