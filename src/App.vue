<template>
  <h1>Little Indian Restro</h1>
  <ul>
    <dish-details
      v-for="dish in dishes"
      :key="dish.id"
      :name="dish.name"
      :description="dish.description"
      :price="dish.price"
      :isFavourite="dish.isFavourite"
      :id="dish.id"
      @toggleFavouriteStatus="toggleFavouriteStatus"
    />
  </ul>
</template>

<script>
import DishDetails from "./components/DishDetails.vue";
export default {
  name: "App",
  components: { DishDetails },
  data() {
    return {
      dishes: [
        {
          id: "avi",
          name: "Butter Chicken 🍗",
          description: "It's finger liking good",
          price: "350",
          isFavourite: true,
        },
        {
          id: "vaibhav",
          name: "Chole Bhature 🥗",
          description:
            " It is a combination of chana masala (spicy white chickpeas) and bhatura/puri, a deep-fried bread made from maida.",
          price: "150",
          isFavourite: false,
        },
        {
          id: "akshata",
          name: "Fish Fry 🎣",
          description:
            " fish fry is a meal containing battered or breaded fried fish.",
          price: "300",
          isFavourite: false,
        },
      ],
    };
  },
  methods: {
    //to get selected dishDetail from child component
    toggleFavouriteStatus(dishID) {
      // console.log("dishId in parent", dishID);
      let identifiedDish = this.dishes.find((dish) => dish.id === dishID);
      //console.log("identifiedDish",identifiedDish);
      identifiedDish.isFavourite = !identifiedDish.isFavourite;
    },
  },
};
</script>

<style>
#app h1{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

   background-color: blueviolet;
}
</style>