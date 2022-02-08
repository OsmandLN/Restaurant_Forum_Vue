<template>
  <div>
    <h2 class="my-4">所有評論：</h2>

    <div v-for="comment in restaurantComments" :key="comment.id">
      <blockquote class="blockquote mb-0">
        <button
          v-if="currentUser.isAdmin"
          @click.stop.prevent="handleDeleteButtonClick(comment.id)"
          type="button"
          class="btn btn-danger float-right"
        >
          Delete
        </button>
        <h3>
          <router-link :to="{ name: 'user', params: { id: comment.User.id } }">
            {{ comment.User.name }}
          </router-link>
        </h3>
        <p>{{ comment.text }}</p>
        <footer class="blockquote-footer">
          {{ comment.createdAt | fromNow }}
        </footer>
      </blockquote>
      <hr />
    </div>
  </div>
</template>

<script>
import { fromNowFilter } from "./../utils/mixins";

const dummyUser = {
  currentUser: {
    id: 1,
    name: "管理者",
    email: "root@example.com",
    image: "https://i.pravatar.cc/300",
    isAdmin: true,
  },
  isAuthenticated: true,
};

export default {
  // 透過mixins屬性將撰寫好的mixin放入
  mixins: [fromNowFilter],

  props: {
    restaurantComments: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      currentUser: dummyUser.currentUser,
    };
  },

  methods: {
    handleDeleteButtonClick(commentId) {
      // 請求API 伺服器刪除 id 為 commentId 的評論
      console.log("handleDeleteButtonClick", commentId);
      // 觸發父層事件 -$emit('事件名稱', 傳遞的資料)
      this.$emit("after-delete-comment", commentId);
    },
  },
};
</script>
