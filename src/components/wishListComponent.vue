<script>
import genreTag from "../components/genreTag.vue";

export default {
  name: "WishListComponent",
  props: ["wishlist"],
  components: {
    genreTag,
  },
  methods: {
    removeMovie(movie) {
      this.$emit("removeMovie", movie);
    },
  },
};
</script>
<template>
  <div class="min-w-32">
    <h1 class="text-center text-lg">Wishlist</h1>
    <ul class="mt-6">
      <li v-for="movie in wishlist" :key="movie">
        <div class="p-2 border-solid border-t-2">
          <div class="text-center font-extrabold text-lg">
            {{ movie.title }}
          </div>
          <div class="flex gap-1">
            <genreTag v-for="genre in movie.genre" :key="genre">{{
              genre
            }}</genreTag>
          </div>
          <div class="flex justify-end mt-1">
            <button
              @click="removeMovie(movie)"
              class="bg-red-500 hover:bg-red-700 text-white font-bold py-1 px-2 rounded-full text-xs"
            >
              Delete
            </button>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>
