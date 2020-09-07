<template>
  <v-app>
    <v-main>
    <BaseLayout/>
    </v-main>
  </v-app>
</template>

<script>
import BaseLayout from './components/BaseLayout'

export default {
  name: 'App',

  components: {
    BaseLayout,
  },

  data: () => ({
    //
  }),
};
</script>
