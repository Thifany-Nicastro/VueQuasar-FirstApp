<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/page1" label="Page One" />
        <q-route-tab to="/page2" label="Page Two" />
        <q-route-tab to="/page3" label="Page Three" />
      </q-tabs>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <q-list>
        <q-item clickable v-ripple :to="{ name: 'Home' }">
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>

          <q-item-section>Home</q-item-section>
        </q-item>

        <q-item clickable v-ripple :to="{ name: 'About' }">
          <q-item-section avatar>
            <q-icon name="info" />
          </q-item-section>

          <q-item-section>About</q-item-section>
        </q-item>

        <q-expansion-item
          icon="inbox"
          label="Inbox"
          default-opened
          :content-inset-level="1"
        >
            <q-item clickable v-ripple :to="{ name: 'Home' }">
              <q-item-section avatar>
                <q-icon name="mail" />
              </q-item-section>

              <q-item-section>Message</q-item-section>
            </q-item>

            <q-item clickable v-ripple :to="{ name: 'Home' }">
              <q-item-section avatar>
                <q-icon name="mail" />
              </q-item-section>

              <q-item-section>Message</q-item-section>
            </q-item>

            <!-- <q-item clickable v-ripple :to="{ name: 'About' }">
              <q-item-section avatar class="q-ml-xl">
                <q-icon color="primary" name="info" />
              </q-item-section>

              <q-item-section>About</q-item-section>
            </q-item> -->
        </q-expansion-item>
        
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
import { nextTick, onMounted, ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
}
</script>