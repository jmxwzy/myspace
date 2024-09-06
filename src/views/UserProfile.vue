<template>
  <BaseContent>
    <div class="row">
      <div class="col-3">
        <!-- v-bind:或:绑定属性 -->
        <!-- v-on:click或@click属性：绑定事件 -->
        <UserProfileInfo @follow="follow" @unfollow="unfollow" :user="user" />
        <UserProfileWrite @post_a_post="post_a_post" />
      </div>
      <div class="col-9">
        <UserProfilePosts :posts="posts" />
      </div>
    </div>
  </BaseContent>
</template>
    
<script>
import { reactive } from "vue";
import BaseContent from "../components/BaseContent";
import UserProfileInfo from "../components/UserProfileInfo";
import UserProfilePosts from "../components/UserProfilePosts";
import UserProfileWrite from "../components/UserProfileWrite";

export default {
  name: "UserProfile",
  components: {
    BaseContent,
    UserProfileInfo,
    UserProfilePosts,
    UserProfileWrite,
  },
  setup() {
    const user = reactive({
      id: 1,
      username: "jmxwzy",
      lastName: "Wang",
      firstName: "Zhenyu",
      followerCount: 0,
      is_followed: false,
    });

    const posts = reactive({
      count: 3,
      posts: [
        {
          id: 1,
          userId: 1,
          content: "test1",
        },
        {
          id: 2,
          userId: 1,
          content: "test2",
        },
        {
          id: 3,
          userId: 1,
          content: "test3",
        },
      ],
    });

    const follow = () => {
      if (user.is_followed) return;
      user.is_followed = true;
      user.followerCount++;
    };

    const unfollow = () => {
      if (!user.is_followed) return;
      user.is_followed = false;
      user.followerCount--;
    };

    const post_a_post = (content) => {
      if (content.value == null) return;
      posts.count++;
      posts.posts.unshift({
        id: posts.count,
        userId: 1,
        content: content,
      });
    };

    return {
      user,
      posts,
      follow,
      unfollow,
      post_a_post,
    };
  },
};
</script>
    
<style scoped>
.container {
  margin-top: 20px;
}
</style>