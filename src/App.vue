<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>APP NAME</span>
        <span class="font-weight-light"> | Cool!</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank">
        <span class="mr-2">Latest Release</span>
      </v-btn>
    </v-toolbar>
    <v-content>
      <boyaaka msg="HALLE"></boyaaka>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import boyaaka from './components/boyaaka'

export default {
  name: 'App',
  components: {
    HelloWorld,
    boyaaka
  },
  data () {
    return {
      //
    }
  }
}
</script>
