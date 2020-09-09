<template>
  <div class="text-center">
    <v-menu
      offset-y
      dark
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          v-bind="attrs"
          v-on="on"
          :block='true'
        >
          Dropdown
        </v-btn>
      </template>
      <v-list
      
      >
        <v-list-item
          v-for="(item, index) in items"
          :key="index"
          @click="greet"
        >
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
  export default {
    name: 'Test',

    data: () => ({
      items: [
        { title: 'Click Me 1' },
        { title: 'Click Me 2' },
        { title: 'Click Me 3' },
        { title: 'Click Me 4' },
      ],
    }),
    methods: {
        greet: function() {
            alert("hello")
        }
    },
  }
</script>