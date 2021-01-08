<template>
  <div class="container">
    <form action="" class="post-input" @submit.prevent="createNewPost">
      <label class="post-input__label" for="newPost">¡Write a post!</label>
      <textarea
        placeholder="Hi! I am a post"
        class="post-input__input shadow"
        name="newPost"
        type="text"
        v-model="newPostContent"
      />
      <button>Post</button>
    </form>
    <div class="post-list">
      <Post
        v-for="post in posts"
        :key="post.id"
        :username="username"
        :post="post"
        :index="post.id"
      />
    </div>
  </div>
</template>
<script>
import Post from "./Post";
export default {
  name: "PostList",
  components: {
    Post,
  },
  props: {
    username: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      newPostContent: "", //Data del v-model
      posts: [
        {
          id: 1,
          content: "This is an example post",
        },
        {
          id: 2,
          content: "First comment",
        },
      ],
    };
  },
  methods: {
    createNewPost() {
      if (this.newPostContent) {
        this.posts.unshift({
          id: this.posts.length + 1,
          content: this.newPostContent,
        });
      }
      this.newPostContent = "";
    },
  },
};
</script>
<style>
.post-input__label {
  display: block;
  margin: 15px 0;
  font-size: 22px;
}
.post-input__input {
    width: 100%;
    border: 0;
    height: 94px;
    padding: 14px;
}
.post-input__input:focus{
    outline: 0;
}
</style>
