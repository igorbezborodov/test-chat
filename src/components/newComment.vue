<template>
  <div class="newComment" v-show="comment">
    <textarea cols="30" rows="3" v-model="text"></textarea>
    <button @click.prevent="sendComment">Отправить сообщение</button>
  </div>
</template>
<script>
import database from "./database.json";

export default {
  name: "newMessage",
  props: ["message", "comment"],
  model: {
    prop: "comment",
    event: "comment-selected",
  },
  data() {
    return {
      list: database,
      text: "",
      id: new Date().valueOf(),
    };
  },
  methods: {
    sendComment: function () {
      this.list.push({
        parentId: this.message.id,
        text: this.text,
        id: this.id,
        children: [],
        rating: 0,
      });
      this.message.children.push(this.id);
      this.text = "";
      this.$emit("comment-selected", false);
    },
  },
};
</script>
<style scoped>
.newComment {
  display: flex;
  align-items: center;
}

button {
  height: 100%;
  width: 100px;
}
</style>