<template>
  <div class="card edit-field">
    <div class="card-body">
      <label for="edit-post" class="form-label">编辑帖子</label>
      <!-- v-model 将 textarea 里的内容和变量 content 绑定到一起：当 content 修改时(通过.value修改)，textarea里的内容也会修改。 -->
      <textarea
        v-model="content"
        class="form-control"
        id="edit-post"
        rows="3"
      ></textarea>
      <button @click="post_a_post" type="button" class="btn btn-primary">
        发帖
      </button>
      <div>{{ content }}</div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "UserProfileWrite",
  setup(props, context) {
    let content = ref("");

    const post_a_post = () => {
      context.emit("post_a_post", content.value);
      content.value = "";
    };

    return {
      content,
      post_a_post,
    };
  },
};
</script>

<style scoped>
.edit-field {
  margin-top: 20px;
}

button {
  margin-top: 10px;
}
</style>