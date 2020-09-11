<template>
  <v-btn @click="openDialog">file select</v-btn>
</template>

<script>
const { dialog } = require("electron").remote;

export default {
  name: "fileSelect",
  methods: {
    openDialog: async function () {
      dialog
        .showOpenDialog({
          title: "Select the folder containing your sequnece files",
          properties: ["openFile", "showHiddenFiles"],
        })
        .then((result) => {
          let userInputFile = result.filePaths;
          alert(userInputFile);
        });
    },
  },
};
</script>

<style scoped></style>
