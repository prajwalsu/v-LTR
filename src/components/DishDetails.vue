<template>
  <li>
    <!-- <h2>{{ name }} {{ dishIsFavourite ? "(Favourite)" : "" }}</h2> -->
    <h2>{{ isFavourite ? "⭐" : "" }} {{ name }} </h2>
    <button @click="toggleFavourite">Toggle Favourite</button>
    <button @click="toggleDetails">
      {{ showDetails ? "Hide " : "Show " }}Details
    </button>
    <ul v-if="showDetails">
      <li>
        <strong>Description</strong>
        {{ description }}
      </li>
      <li>
        <strong>Price</strong>
        {{ price }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  emits: ["toggleFavouriteStatus"],
  //   props: ["name", "description", "price", "isFavourite"],
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    price: {
      type: String,
      required: true,
    },
    isFavourite: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      //   dishIsFavourite: this.isFavourite,
      showDetails: false,
    };
  },
  methods: {
    toggleFavourite() {
      //   this.dishIsFavourite = !this.dishIsFavourite;

      //   if (this.dishIsFavourite) {
      //     this.dishIsFavourite = false;
      //   } else {
      //     this.dishIsFavourite = true;
      //   }
      this.$emit("toggleFavouriteStatus", this.id);
    },
    toggleDetails() {
      this.showDetails = !this.showDetails;
    },
  },
};
</script>

<style>
li {
  list-style-type: none;
}
</style>