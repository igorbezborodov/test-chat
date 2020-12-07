<template>
  <div id="rating">
    <div
      class="arrow like"
      :style="{ 'border-color': likeColor }"
      @click="takeLike"
    ></div>
    <p class="count">{{ message.rating }}</p>
    <div
      class="arrow dislike"
      :style="{ 'border-color': dislikeColor }"
      @click="takeDislike"
    ></div>
  </div>
</template>

<script>
export default {
  name: "rating",
  props: ["message"],
  data: function () {
    return {
      likeColor: "grey",
      dislikeColor: "grey",
    };
  },
  methods: {
    takeLike: function () {
      if (this.likeColor == "grey" && this.dislikeColor == "grey") {
        this.likeColor = "green";
      } else if (this.likeColor == "grey" && this.dislikeColor == "red") {
        this.dislikeColor = "grey";
      }
      return this.likeColor, this.dislikeColor, this.message.rating++;
    },
    takeDislike: function () {
      if (this.likeColor == "grey" && this.dislikeColor == "grey") {
        this.dislikeColor = "red";
      } else if (this.likeColor == "green" && this.dislikeColor == "grey") {
        this.likeColor = "grey";
      }
      return this.likeColor, this.dislikeColor, this.message.rating--;
    },
  },
};
</script>

<style scoped>
#rating {
  display: flex;
  width: 40px;
  justify-content: space-between;
  align-items: center;
}

.arrow {
  border: solid;
  border-color: grey;
  border-width: 0 3px 3px 0;
  display: inline-block;
  padding: 3px;
  cursor: pointer;
  height: 1px;
}

.like {
  transform: rotate(-135deg);
}

.dislike {
  transform: rotate(45deg);
}

.count {
  margin: 0 2px;
  font-size: 15px;
}
</style>