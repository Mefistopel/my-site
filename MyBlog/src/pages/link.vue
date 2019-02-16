<template>
  <q-page class="flex ">
    <q-card>
      <q-list>
        <q-item>
          <q-item-side>
            <q-item-tile color="primary" icon="local bar" />
          </q-item-side>
          <q-item-main>
            <q-item-tile label>Bar XYZ</q-item-tile>
            <q-item-tile sublabel>Have a drink.</q-item-tile>
          </q-item-main>
        </q-item>
        <q-item>
          <q-item-side>
            <q-item-tile color="red" icon="local gas station" />
          </q-item-side>
          <q-item-main>
            <q-item-tile label>Gas Station</q-item-tile>
            <q-item-tile sublabel>Fill your gas tank.</q-item-tile>
          </q-item-main>
        </q-item>
        <q-item>
          <q-item-side>
            <q-item-tile color="amber" icon="local movies" />
          </q-item-side>
          <q-item-main>
            <q-item-tile label>Cinema XYZ</q-item-tile>
            <q-item-tile sublabel>Watch a movie.</q-item-tile>
          </q-item-main>
        </q-item>
      </q-list>
      ...
    </q-card>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex'
}
</script>
