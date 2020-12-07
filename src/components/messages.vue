<template>
  <div id="message">
    <p class="text">{{ message.text }}</p>
    <div class="options">
      <p class="btn" @click="isDisable = !isDisable">
        Комментарии ( {{ message.children.length }} )
      </p>
      <rating :message="message" />
    </div>
    <div class="comments" v-if="!isDisable">
      <div
        v-for="(item, i) in data"
        v-show="item.parentId === message.id"
        :key="i"
      >
        <messages :message="item" />
      </div>
      <div class="new-comment">
        <p v-show="!isComment" @click="isComment = !isComment">
          Комментировать
        </p>
        <new-comment :message="message" v-model="isComment" />
      </div>
    </div>
  </div>
</template>
<script>
import database from "./database.json";
import newComment from "./newComment.vue";
import rating from "./rating.vue";

export default {
  components: { newComment, rating },
  name: "messages",
  props: ["message"],
  data() {
    return {
      isDisable: true,
      data: database,
      isComment: false,
    };
  },
};
</script>
<style scoped>
.text {
  margin-bottom: 0;
  font-size: 26px;
}

.options {
  margin-top: -5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 170px;
}

.btn {
  font-size: 13px;
  color: grey;
  cursor: pointer;
}

.comments {
  margin-left: 50px;
}

.new-comment {
  margin-left: -50px;
}
</style>