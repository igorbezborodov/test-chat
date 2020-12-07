<template>
  <div id="chat">
    <div class="messages">
      <div v-for="(item, i) in data" v-show="item.parentId === null" :key="i">
        <messages :message="item" />
      </div>
    </div>
    <new-message />
  </div>
</template>
<script>
import database from "./database.json";
import messages from "./messages.vue";
import NewMessage from "./newMessage.vue";

export default {
  name: "chat",
  components: {
    messages,
    NewMessage,
  },
  data() {
    return {
      data: database,
    };
  },
};
</script>
<style scoped>
#chat {
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-between;
  height: 90vh;
}
</style>