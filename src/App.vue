<template>
  <div id="app">
    <chat />
  </div>
</template>

<script>
import chat from "./components/chat.vue";

export default {
  name: "App",
  components: {
    chat,
  },
};
</script>