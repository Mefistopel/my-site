<template>
  <q-page class="flex justify-center">
    <q-card
      dark
      class="q-ma-md items-right"
      text-color="grey-3"
      inline
      style="width: 900px"
      :style="{'background-color': '#6A1B9A'}" >
      <q-card-title>
        Резюме
        <span slot="subtitle">Пишем идеальное резюме вместе!</span>
        <div
          slot="right"
          class="row items-center">
          <q-pagination
            color="secondary"
            text-color="red"
            input
            v-model="page"
            :min="1"
            :max="6" />
        </div>
      </q-card-title>
      <q-card-separator />
      <q-card-main>
        <div v-show="page == 1">
          <div class="row justify-around">
            <q-input
              dark
              color="secondary"
              v-model="lastName"
              float-label="Фамилия">
              <q-tooltip :delay="500" >Например: Янусов</q-tooltip>
            </q-input>
            <q-input
              dark
              color="secondary"
              v-model="firstName"
              float-label="Имя">
              <q-tooltip :delay="500" >Например: Андрей</q-tooltip>
            </q-input>
            <q-input
              dark
              color="secondary"
              v-model="middleName"
              float-label="Отчество">
              <q-tooltip :delay="500" >Например: Сергеевич</q-tooltip>
            </q-input>
          </div>

          <br><br><br>

          <div class="row justify-around">
            <q-datetime
              dark
              color="secondary"
              float-label="Дата рождения"
              v-model="brithData"
              type="date" />
            <q-input
              dark
              color="secondary"
              float-label="Место рождения"
              v-model.number="indexPR">
              <q-tooltip :delay="500" >Например: Московская обл., г. Москва</q-tooltip>
            </q-input>
          </div>

          <br><br><br>

          <div class="row justify-around">
            <q-input
              dark
              type="textarea"
              color="secondary"
              float-label="Адрес проживания"
              v-model="address"
              class="col-8">
              <q-tooltip :delay="500" >Например: Московская обл., г. Москва, ул. Янусова, д. 15, кв. 12</q-tooltip>
            </q-input>
            <q-input
              dark
              color="secondary"
              float-label="Индекс (по почте России)"
              :count="6"
              v-model.number="indexPR"/>
          </div>

          <br><br><br>

          <div class="row justify-around">
            <q-input
              dark
              color="secondary"
              float-label="Семейное положение"
              v-model.number="indexPR">
              <q-tooltip :delay="500" >Например: холост</q-tooltip>
            </q-input>
          </div>
        </div>
        <div v-show="page == 2">
          <h5>Образование</h5>
        </div>

        <br>
        <q-btn
          class="justify justify-center"
          @click="toPDF"
          color="secondary"
          icon="save"
          label="Скачать резюме" />
      </q-card-main>
    </q-card>
  </q-page>
</template>

<style>
</style>

<script>
import JSPDF from 'jspdf'

export default {
  name: 'PageIndex',
  data () {
    return {
      firstName: '',
      lastName: '',
      middleName: '',
      indexPR: '',
      address: '',
      brithData: null,
      page: 1
    }
  },
  methods: {
    toPDF () {
      let pdfName = 'Резюме ' + this.firstName
      var doc = new JSPDF()
      doc.text(this.lastName + ' ' + this.firstName + ' ' + this.middleName, 10, 10)
      doc.save(pdfName + '.pdf')
    },
    notify () {
      this.$q.notify({
        message: `Упс! Данный функционал пока отсутсвует.`,
        timeout: 1000, // in milliseconds; 0 means no timeout
        type: 'warning',
        textColor: 'black',
        icon: 'build',
        detail: 'Разрабатывается...',
        position: 'center'
      })
    }
  }
}
</script>
