<template>
  <q-layout view="hHh lpR fFf">

    <q-header bordered elevated class="bg-white text-black">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="left = !left" />

        <q-toolbar-title class="text-black text-bold">
          <q-avatar class="q-mr-sm">
            <img src="../assets/logo.svg">
          </q-avatar>
          Trading Helper
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="left" width="200" bordered side="left">
      <!-- drawer content -->
      <q-item :to="{ name: 'Home' }" clickable v-ripple :active="this.$route.name === 'Home'" active-class="text-red">
        <q-item-section avatar>
          <q-icon name="home" />
        </q-item-section>

        <q-item-section>
          Home
        </q-item-section>
      </q-item>

      <q-item :to="{ name: 'My Trades' }" clickable v-ripple :active="this.$route.name === 'My Trades'" active-class="text-red">
        <q-item-section avatar>
          <q-icon name="request_quote" />
        </q-item-section>

        <q-item-section>
          My Trades
        </q-item-section>
      </q-item>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
export default {
  data () {
    return {
      left: false
    }
  }
}
</script>
