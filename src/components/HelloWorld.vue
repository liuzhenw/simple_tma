<template>
  <div class="hello">
    <h1>{{ props.msg }}</h1>
    <button @click="showPopup">ShowPopup</button>
    
  </div>
</template>

<script setup>
import WebApp from "@twa-dev/sdk";
import { defineProps } from "vue";
const props = defineProps({
  msg: {
    type: String,
    default: "",
  },
});

const showPopup = () => {
  WebApp.showPopup(
    {
      title: "Title",
      message: "This is a popup message",
      buttons: [
        { id: "link", type: "default", text: "Open ton.org" },
        { type: "cancel" },
      ],
    },
    (buttonId) => {
      if (buttonId === "link") {
        WebApp.openLink("https://ton.org");
      }
    }
  );
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
