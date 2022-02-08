<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.categoryName }}
      </span>
    </div>

    <hr />

    <ul>
      <li>評論數： {{ restaurant.commentsLength }} </li>
      <li>瀏覽次數： {{ restaurant.viewCounts }} </li>
    </ul>

    <button type="button" class="btn btn-link" @click="$router.back()">
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
  restaurant: {
    id: 1,
    name: "London Cruickshank",
    tel: "710-373-4387",
    address: "467 Kling Port",
    opening_hours: "08:00",
    description:
      "Veritatis a nobis ut sapiente aut sunt architecto. Fugit quam aut. Eligendi rem cumque eos sequi aut quis doloribus voluptatem voluptatum. Rem et maxime ad voluptatem qui beatae excepturi ipsa incidunt. Quisquam in quae excepturi adipisci.",
    image:
      "https://loremflickr.com/320/240/restaurant,food/?random=68.60056138699827",
    viewCounts: 1,
    createdAt: "2022-01-26T10:08:44.000Z",
    updatedAt: "2022-02-02T15:30:25.000Z",
    CategoryId: 2,
    Category: {
      id: 2,
      name: "日本料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
    Comments: [
      {
        id: 1,
        text: "Deleniti quam quisquam culpa accusamus exercitationem hic nisi.",
        UserId: 1,
        RestaurantId: 1,
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
        User: {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$mqovNlI3Zep7eMd3GkdL7.HNQ0yOPZ.j.JS6g0D05a/ert.9yMUvK",
          isAdmin: true,
          image: null,
          createdAt: "2022-01-26T10:08:43.000Z",
          updatedAt: "2022-01-26T10:08:43.000Z",
        },
      },
      {
        id: 51,
        text: "Voluptatem quod praesentium temporibus necessitatibus perspiciatis.",
        UserId: 1,
        RestaurantId: 1,
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
        User: {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$mqovNlI3Zep7eMd3GkdL7.HNQ0yOPZ.j.JS6g0D05a/ert.9yMUvK",
          isAdmin: true,
          image: null,
          createdAt: "2022-01-26T10:08:43.000Z",
          updatedAt: "2022-01-26T10:08:43.000Z",
        },
      },
      {
        id: 101,
        text: "Quo et nulla optio omnis nihil sit.",
        UserId: 2,
        RestaurantId: 1,
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
        User: {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$TamWCUoI.S77h5yHI0tgLeZJNHvYOKqhJ6a6WtaEfIZGzScLaRDjq",
          isAdmin: false,
          image: null,
          createdAt: "2022-01-26T10:08:43.000Z",
          updatedAt: "2022-01-26T10:08:43.000Z",
        },
      },
    ],
  },
};

export default {
  data() {
    return {
      restaurant: " ",
    };
  },
  methods: {
    fetchRestDashboard() {
      this.restaurant = {
        ...dummyData.restaurant,
        categoryName: dummyData.restaurant.Category.name,
        commentsLength: dummyData.restaurant.Comments.length,
        viewCounts: dummyData.restaurant.viewCounts,
      };
    },
  },
  created() {
    this.fetchRestDashboard();
  },
};
</script>
