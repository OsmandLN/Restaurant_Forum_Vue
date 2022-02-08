<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">人氣餐廳</h1>

    <hr />
    <RestaurantsTopCard
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      :initial-restaurant="restaurant"
    />
    <!-- <div class="card mb-3" style="max-width: 540px; margin: auto">
      <div class="row no-gutters">
        <div class="col-md-4">
          <a href="#">
            <img
              class="card-img"
              src="https://loremflickr.com/320/240/food,dessert,restaurant/?random=2"
            />
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">Mrs. Mckenzie Johnston</h5>
            <span class="badge badge-secondary">收藏數：0</span>
            <p class="card-text">
              Quia pariatur perferendis architecto tenetur omnis
            </p>
            <a href="#" class="btn btn-primary mr-2">Show</a>

            <button type="button" class="btn btn-danger mr-2">移除最愛</button>
            <button type="button" class="btn btn-primary">加到最愛</button>
          </div>
        </div>
      </div>
    </div> -->
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs";
import RestaurantsTopCard from "./../components/RestaurantsTopCard";

const dummyData = {
  restaurants: [
    {
      id: 50,
      name: "Conrad Halvorson",
      tel: "779-216-6951",
      address: "0433 Forrest Union",
      opening_hours: "08:00",
      description: "Dolore veritatis minus quidem doloribus.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=66.62327863530994",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 5,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 49,
      name: "Uriel Legros",
      tel: "648.280.3963",
      address: "7096 Winston Spur",
      opening_hours: "08:00",
      description: "Et reiciendis fugit impedit tenetur corporis moles",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=82.26669580206445",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 5,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 48,
      name: "Clovis Boyer",
      tel: "521-714-4753 x837",
      address: "91694 Gibson Neck",
      opening_hours: "08:00",
      description: "Tenetur eos dignissimos et minus.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=84.21082461317162",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 47,
      name: "Ally Veum",
      tel: "(482) 984-5611",
      address: "7272 Watsica Mountains",
      opening_hours: "08:00",
      description: "neque",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=47.27381479033086",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 46,
      name: "Jude Schowalter",
      tel: "395.018.9299",
      address: "0949 Nikolaus Turnpike",
      opening_hours: "08:00",
      description: "Aut expedita ullam quos dicta. Quae perferendis co",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=33.57711381911959",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 45,
      name: "Mr. Alejandrin Sauer",
      tel: "(019) 565-2291 x336",
      address: "9662 Grady Station",
      opening_hours: "08:00",
      description: "In aliquid suscipit vel sunt atque sunt.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=42.23390445854993",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 44,
      name: "Mozelle Graham",
      tel: "183.917.1291 x235",
      address: "594 John Forks",
      opening_hours: "08:00",
      description: "Recusandae deserunt ut omnis porro qui quia dolore",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=20.79465807417815",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 5,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 43,
      name: "Joaquin Kuhic",
      tel: "096.612.4864",
      address: "379 Conroy Lodge",
      opening_hours: "08:00",
      description: "Exercitationem consequatur rem maxime expedita. Vo",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=25.061010359969348",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 42,
      name: "Dayana Dare",
      tel: "069-789-1951",
      address: "622 Wilderman Knolls",
      opening_hours: "08:00",
      description: "Odit voluptatem nemo dolores accusantium distincti",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=18.19000717987096",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 41,
      name: "Malcolm VonRueden II",
      tel: "405-292-3099 x519",
      address: "586 Paucek Squares",
      opening_hours: "08:00",
      description: "Voluptas beatae numquam sed nam impedit saepe tene",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=13.607706514273254",
      viewCounts: 0,
      createdAt: "2022-01-26T10:08:44.000Z",
      updatedAt: "2022-01-26T10:08:44.000Z",
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
  ],
};

export default {
  components: {
    NavTabs,
    RestaurantsTopCard,
  },

  data() {
    return {
      restaurants: [],
    };
  },

  created() {
    this.fetchTopRestaurants();
  },

  methods: {
    fetchTopRestaurants() {
      const { restaurants } = dummyData;
      this.restaurants = restaurants;
    },
  },
};
</script>
