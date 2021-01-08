<template>
  <div class="post-list__post shadow">
    <p class="post-list__post-content">{{ post.content }}</p>
    <small class="post-list_post-username">@{{ username }}</small>
  </div>
</template>
<script>
export default {
  name: "Post",
  props: {
    username: {
      type: String,
      required: true,
    },
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>
<style>
.post-list__post {
  background: white;
  margin-bottom: 12px;
  padding: 16px 20px;
  border-radius: 7px;
}
</style>
