<template>
  <div class="container py-5">
    <!-- use NavTabs component -->
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />

    <div class="row text-center">
      <!-- 美食達人卡片 UserTopCard-->
      <UsersTopCard v-for="user in users" :key="user.id" :initial-user="user" />
    </div>

    <!-- 分頁標籤 RestaurantPagination
    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="categoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    /> -->
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs";
import UsersTopCard from "./../components/UsersTopCard";

const dummyData = {
  users: [
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$mqovNlI3Zep7eMd3GkdL7.HNQ0yOPZ.j.JS6g0D05a/ert.9yMUvK",
      isAdmin: true,
      image: "https://i.pravatar.cc/150?img=3",
      createdAt: "2022-01-26T10:08:43.000Z",
      updatedAt: "2022-01-26T10:08:43.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$TamWCUoI.S77h5yHI0tgLeZJNHvYOKqhJ6a6WtaEfIZGzScLaRDjq",
      isAdmin: false,
      image: "https://i.pravatar.cc/150?img=2",
      createdAt: "2022-01-26T10:08:43.000Z",
      updatedAt: "2022-01-26T10:08:43.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$aRmBd.zXlyXlCPp6jWHhmOGFWrsL4dameoqmvjr9i215TJ6MkO8xy",
      isAdmin: false,
      image: "https://i.pravatar.cc/150?img=1",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
  ],
};

export default {
  components: {
    NavTabs,
    UsersTopCard,
  },
  data() {
    return {
      users: [],
    };
  },
  created() {
    this.fetchTopUsers();
  },
  methods: {
    fetchTopUsers() {
      const { users } = dummyData;
      this.users = users;
    },
  },
};
</script>
