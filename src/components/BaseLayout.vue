<template>
  <v-app id="inspire">
    <WorkFlow/>
    <v-navigation-drawer
      fixed
      v-model="drawer"
      app
      clipped
    >
      <v-list dense>
        <SidebarButton/>
        <Test/>
      </v-list>
    </v-navigation-drawer>
    
    <v-app-bar
      app
      clipped-left
      fixed
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>PIPECRAFT II</v-toolbar-title>
    </v-app-bar>
        
    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
  import Test from './Test'
  import WorkFlow from './WorkFlow'
  import SidebarButton from './SidebarButton'

  export default {
    components: {
        SidebarButton,
        WorkFlow,
        Test,
    },
    name: 'BaseLayout',
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
    }),
    created () {
      this.$vuetify.theme.dark = true
    },
  }
</script>