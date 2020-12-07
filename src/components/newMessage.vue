<template>
  <div class="newMesage">
    <textarea cols="30" rows="3" v-model="text"></textarea>
    <button @click.prevent="sendMessage">Отправить сообщение</button>
  </div>
</template>
<script>
import database from "./database.json";

export default {
  name: "newMessage",
  data() {
    return {
      list: database,
      text: "",
    };
  },
  methods: {
    sendMessage: function () {
      return (
        this.list.push({
          parentId: null,
          text: this.text,
          id: new Date().valueOf(),
          children: [],
          rating: 0,
        }),
        (this.text = "")
      );
    },
  },
};
</script>
<style scoped>
.newMesage {
  display: flex;
  align-items: center;
}

button {
  height: 100%;
  width: 100px;
}
</style>