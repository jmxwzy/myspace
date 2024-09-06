<template>
  <div class="card">
    <div class="card-body">
      <div class="row">
        <div class="col-3">
          <img
            class="img-fluid"
            src="https://cdn.acwing.com/media/user/profile/photo/83171_lg_e23e33f952.jpg"
            alt=""
          />
        </div>
        <div class="col-9">
          <div class="username">{{ fullName }}</div>
          <div class="fans">粉丝: {{ user.followerCount }}</div>
          <button
            @click="follow"
            v-if="!user.is_followed"
            type="button"
            class="btn btn-secondary btn-sm"
          >
            +关注
          </button>
          <button
            @click="unfollow"
            v-if="user.is_followed"
            type="button"
            class="btn btn-secondary btn-sm"
          >
            取消关注
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  name: "UserProfileInfo",
  props: {
    // 存储父组件传递给子组件的数据
    user: {
      type: Object,
      required: true,
    },
  },
  setup(props, context) {
    // computed：动态计算某个数据
    let fullName = computed(
      () => props.user.lastName + " " + props.user.firstName
    );

    const follow = () => {
      // context.emit()：触发父组件绑定的函数
      context.emit("follow");
    };

    const unfollow = () => {
      context.emit("unfollow");
    };

    return {
      fullName,
      follow,
      unfollow,
    };
  },
};
</script>

<style scoped>
img {
  border-radius: 50%;
}

.username {
  font-weight: bold;
}

.fans {
  font-size: 12px;
  color: grey;
}

button {
  padding: 2px 4px;
  font-size: 12px;
}
</style>