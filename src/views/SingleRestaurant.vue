<template>
  <div class="container py-5">
    <!-- 餐廳資訊頁 RestaurantDetail -->
    <RestaurantDetail :initial-restaurant="restaurant" />
    <hr />
    <!-- 餐廳評論 RestaurantComments -->
    <RestaurantComments
      :restaurant-comments="restaurantComments"
      @after-delete-comment="afterDeleteComment"
    />
    <!-- 新增評論 CreateComment -->
    <CreateComment
      :restaurant-id="restaurant.id"
      @after-create-comment="afterCreateComment"
    />
  </div>
</template>

<script>
import RestaurantDetail from "./../components/RestaurantDetail";
import RestaurantComments from "./../components/RestaurantComments";
import CreateComment from "./../components/CreateComment";

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
    updatedAt: "2022-02-02T15:30:25.522Z",
    CategoryId: 2,
    Category: {
      id: 2,
      name: "日本料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
    FavoritedUsers: [],
    LikedUsers: [],
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
  isFavorited: false,
  isLiked: false,
};

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
  components: {
    RestaurantDetail,
    RestaurantComments,
    CreateComment,
  },

  data() {
    return {
      restaurant: {
        id: -1,
        name: "",
        categoryName: "",
        image: "",
        openingHours: "",
        tel: "",
        address: "",
        description: "",
        isFavorited: false,
        isLiked: false,
      },
      currentUser: dummyUser.currentUser,
      restaurantComments: [],
    };
  },

  created() {
    const { id: restaurantId } = this.$route.params;
    this.fetchSingleRestaurant(restaurantId);
  },

  methods: {
    fetchSingleRestaurant(restaurantId) {
      console.log("fetchSingleRestaurant id: ", restaurantId);

      this.restaurant = {
        id: dummyData.restaurant.id,
        name: dummyData.restaurant.name,
        categoryName: dummyData.restaurant.Category.name,
        image: dummyData.restaurant.image,
        openingHours: dummyData.restaurant.opening_hours,
        tel: dummyData.restaurant.tel,
        address: dummyData.restaurant.address,
        description: dummyData.restaurant.description,
        isFavorited: dummyData.isFavorited,
        isLiked: dummyData.isLiked,
      };

      this.restaurantComments = dummyData.restaurant.Comments;
    },

    afterDeleteComment(commentId) {
      //使用filter方法留下id不等於commentId的 comment
      this.restaurantComments = this.restaurantComments.filter(
        (comment) => comment.id !== commentId
      );
    },

    afterCreateComment(payload) {
      const { commentId, restaurantId, text } = payload;
      this.restaurantComments.push({
        id: commentId,
        RestaurantId: restaurantId,
        User: {
          id: this.currentUser.id,
          name: this.currentUser.name,
        },
        text: text,
        createdAt: new Date(),
      });
    },
  },
};
</script>
