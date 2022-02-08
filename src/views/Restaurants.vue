<template>
  <div class="container py-5">
    <!-- use NavTabs component -->
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />
    <div class="row">
      <!-- 餐廳卡片 RestaurantCard-->
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <!-- 分頁標籤 RestaurantPagination -->
    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="categoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs";
import RestaurantCard from "./../components/RestaurantCard";
import RestaurantsNavPills from "./../components/RestaurantsNavPills";
import RestaurantsPagination from "./../components/RestaurantsPagination";

const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "London Cruickshank",
      tel: "710-373-4387",
      address: "467 Kling Port",
      opening_hours: "08:00",
      description: "Veritatis a nobis ut sapiente aut sunt architecto.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=68.60056138699827",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 2,
      name: "Beth Block",
      tel: "161.829.6567",
      address: "49209 Anais Route",
      opening_hours: "08:00",
      description: "Est earum quasi sunt veniam beatae. Itaque fuga eo",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=3.7826172115070555",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 3,
      name: "Nelle Goodwin",
      tel: "548-892-0000 x4105",
      address: "547 Reymundo Spurs",
      opening_hours: "08:00",
      description: "Earum aut quia quia aut voluptas pariatur pariatur",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=19.226769049060266",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: "Carlee Schinner V",
      tel: "107-127-9270 x3193",
      address: "579 Clare Club",
      opening_hours: "08:00",
      description: "Harum enim ea qui aut nihil aut incidunt officia. ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=22.5374598126157",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: "Marquis O'Kon",
      tel: "(463) 867-0952",
      address: "429 Magali Skyway",
      opening_hours: "08:00",
      description: "Quasi quo alias aut ut omnis modi atque voluptate ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=92.08004297577395",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 6,
      name: "Sebastian Turcotte",
      tel: "(257) 224-4556",
      address: "758 Auer Highway",
      opening_hours: "08:00",
      description: "Voluptas labore ea consequatur. Ea velit consectet",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=18.221838070751616",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: "Jacinto Towne DDS",
      tel: "684.533.0650 x835",
      address: "951 Braun Stravenue",
      opening_hours: "08:00",
      description: "Officia nihil est quibusdam qui quis.\nSint blandit",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=41.8553263353691",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 8,
      name: "Laney Franecki",
      tel: "171-898-8267",
      address: "402 Auer Meadows",
      opening_hours: "08:00",
      description: "Sint fugit iusto distinctio natus vero at impedit ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=72.87697146904443",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 9,
      name: "Miller Ratke Sr.",
      tel: "815.336.6782 x27630",
      address: "5059 Gaylord Overpass",
      opening_hours: "08:00",
      description: "Eum ab quis impedit quos ea ex quisquam exercitati",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=16.491242010329277",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: "Mr. Karina Reilly",
      tel: "901-733-3618",
      address: "785 Claude Shores",
      opening_hours: "08:00",
      description: "enim perspiciatis modi",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=29.656666626241666",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-26T10:08:44.000Z",
        updatedAt: "2022-01-26T10:08:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: "中式料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
    {
      id: 2,
      name: "日本料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
    {
      id: 7,
      name: "複合式料理",
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
    },
  ],
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
  categoryId: "",
};

export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination,
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1,
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next,
      } = dummyData;
      this.restaurants = restaurants;
      this.categories = categories;
      this.categoryId = categoryId;
      this.currentPage = page;
      this.totalPage = totalPage;
      this.previousPage = prev;
      this.nextPage = next;
    },
  },
};
</script>
