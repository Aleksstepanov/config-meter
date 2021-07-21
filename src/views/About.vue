<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>{{ title }}</p>
  </div>
</template>

<script>
import { ipcRenderer } from "electron";
export default {
  name: "About",

  data() {
    return {
      title: "",
    };
  },

  async mounted() {
    ipcRenderer.send("mounted", "I am monted");
    ipcRenderer.on("python", async (ev, arg) => {
      this.title = await arg[0];
    });
  },
};
</script>
