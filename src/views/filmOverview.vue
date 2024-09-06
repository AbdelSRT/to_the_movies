<script>
import wishListComponent from "../components/wishListComponent.vue";
import genreTag from "../components/genreTag.vue";
import Cookies from "js-cookie";

export default {
  components: {
    wishListComponent,
    genreTag,
  },
  data() {
    return {
      wishlist: [],
      films: [
        {
          title: "The Shawshank Redemption",
          year: 1994,
          description:
            "A Maine banker convicted of the murder of his wife and her lover in 1947 gradually forms a friendship over a quarter century with a hardened convict, while maintaining his innocence and trying to remain hopeful through simple compassion.",
          director: "Frank Darabont",
          duration: "2h 22min",
          genre: ["Drama"],
          rate: 9.3,
          picture:
            "https://m.media-amazon.com/images/S/pv-target-images/a954a605b05d414e7d2d7a9afad4c1e78c44fb7bce2a83607baf6b3ae82f0257.jpg",
        },
        {
          title: "The Godfather",
          year: 1972,
          description:
            "The aging patriarch of an organized crime dynasty transfers control of his clandestine empire to his reluctant son.",
          director: "Francis Ford Coppola",
          duration: "2h 55min",
          genre: ["Crime", "Drama"],
          rate: 9.2,
          picture:
            "https://m.media-amazon.com/images/M/MV5BM2MyNjYxNmUtYTAwNi00MTYxLWJmNWYtYzZlODY3ZTk3OTFlXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_FMjpg_UX1000_.jpg",
        },
        {
          title: "The Dark Knight",
          year: 2008,
          description:
            "When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, Batman, James Gordon and Harvey Dent must work together to put an end to the madness.",
          director: "Christopher Nolan",
          duration: "2h 32min",
          genre: ["Action", "Crime", "Drama", "Thriller"],
          rate: 9.0,
          picture:
            "https://upload.wikimedia.org/wikipedia/en/1/1c/The_Dark_Knight_%282008_film%29.jpg",
        },
        {
          title: "Inception",
          year: 2010,
          description:
            "A thief who steals corporate secrets through the use of dream-sharing technology is given the inverse task of planting an idea into the mind of a C.E.O., but his tragic past may doom the project and his team to disaster.",
          director: "Christopher Nolan",
          duration: "2h 28min",
          genre: ["Action", "Adventure", "Sci-Fi"],
          rate: 8.8,
          picture:
            "https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_QL75_UX190_CR0,0,190,281_.jpg",
        },
        {
          title: "The Lord of the Rings: The Return of the King",
          year: 2003,
          description:
            "Gandalf and Aragorn lead the World of Men against Sauron's army to draw his gaze from Frodo and Sam as they approach Mount Doom with the One Ring.",
          director: "Peter Jackson",
          duration: "3h 21min",
          genre: ["Adventure", "Drama", "Fantasy"],
          rate: 8.9,
          picture:
            "https://m.media-amazon.com/images/M/MV5BNzA5ZDNlZWMtM2NhNS00NDJjLTk4NDItYTRmY2EwMWZlMTY3XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_QL75_UX190_CR0,0,190,281_.jpg",
        },
        {
          title: "Pulp Fiction",
          year: 1994,
          description:
            "The lives of two mob hitmen, a boxer, a gangster and his wife, and a pair of diner bandits intertwine in four tales of violence and redemption.",
          director: "Quentin Tarantino",
          duration: "2h 34min",
          genre: ["Crime", "Drama"],
          rate: 8.9,
          picture:
            "https://musicart.xboxlive.com/7/767c6300-0000-0000-0000-000000000002/504/image.jpg?w=1920&h=1080",
        },
        {
          title: "Fight Club",
          year: 1999,
          description:
            "An insomniac office worker and a devil-may-care soap maker form an underground fight club that evolves into much more.",
          director: "David Fincher",
          duration: "2h 19min",
          genre: ["Drama"],
          rate: 8.8,
          picture:
            "https://m.media-amazon.com/images/M/MV5BOTgyOGQ1NDItNGU3Ny00MjU3LTg2YWEtNmEyYjBiMjI1Y2M5XkEyXkFqcGc@._V1_.jpg",
        },
        {
          title: "The Matrix",
          year: 1999,
          description:
            "When a beautiful stranger leads computer hacker Neo to a forbidding underworld, he discovers the shocking truth--the life he knows is the elaborate deception of an evil cyber-intelligence.",
          director: "Lana Wachowski, Lilly Wachowski",
          duration: "2h 16min",
          genre: ["Action", "Sci-Fi"],
          rate: 8.7,
          picture:
            "https://upload.wikimedia.org/wikipedia/en/c/c1/The_Matrix_Poster.jpg",
        },
        {
          title: "Interstellar",
          year: 2014,
          description:
            "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
          director: "Christopher Nolan",
          duration: "2h 49min",
          genre: ["Adventure", "Drama", "Sci-Fi"],
          rate: 8.6,
          picture:
            "https://upload.wikimedia.org/wikipedia/en/b/bc/Interstellar_film_poster.jpg",
        },
        {
          title: "The Avengers",
          year: 2012,
          description:
            "Earth's mightiest heroes must come together and learn to fight as a team if they are going to stop the mischievous Loki and his alien army from enslaving humanity.",
          director: "Joss Whedon",
          duration: "2h 23min",
          genre: ["Action", "Adventure", "Sci-Fi"],
          rate: 8.0,
          picture:
            "https://m.media-amazon.com/images/M/MV5BNDYxNjQyMjAtNTdiOS00NGYwLWFmNTAtNThmYjU5ZGI2YTI1XkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg",
        },
        {
          title: "The Social Network",
          year: 2010,
          description:
            "As Harvard student Mark Zuckerberg creates the social networking site that would become known as Facebook, he is sued by the twins who claimed he stole their idea, and by the co-founder who was later squeezed out of the business.",
          director: "David Fincher",
          duration: "2h",
          genre: ["Biography", "Drama"],
          rate: 7.7,
          picture:
            "https://www.sonypictures.com/sites/default/files/styles/max_560x840/public/chameleon/title-movie/DP_1654052_TC_1400x2100_625139_SOCIAL%20NETWORK%2C%20THE_2000x3000_English%20%28US%29_0.jpg?itok=hkayPoaY",
        },
        {
          title: "The Lion King",
          year: 1994,
          description:
            "Lion prince Simba and his father are targeted by his bitter uncle, who wants to ascend the throne himself.",
          director: "Roger Allers, Rob Minkoff",
          duration: "1h 28min",
          genre: ["Animation", "Adventure", "Drama"],
          rate: 8.5,
          picture:
            "https://upload.wikimedia.org/wikipedia/en/3/3d/The_Lion_King_poster.jpg",
        },
        {
          title: "The Pursuit of Happyness",
          year: 2006,
          description:
            "A struggling salesman takes custody of his son as he's poised to begin a life-changing professional career.",
          director: "Gabriele Muccino",
          duration: "1h 57min",
          genre: ["Biography", "Drama"],
          rate: 8.0,
          picture:
            "https://upload.wikimedia.org/wikipedia/en/8/81/Poster-pursuithappyness.jpg",
        },
      ],
    };
  },
  methods: {
    addToWishlist(film) {
      const wishlistItem = {
        title: film.title,
        genre: film.genre,
      };
      this.wishlist.push(wishlistItem);
      this.updateWishlistCookie();
    },
    removeFromWishlist(film) {
      this.wishlist = this.wishlist.filter((item) => item.title !== film.title);
      this.updateWishlistCookie();
    },
    isInWishlist(film) {
      return this.wishlist.some((item) => item.title === film.title);
    },
    updateWishlistCookie() {
      Cookies.set("wishlist", JSON.stringify(this.wishlist), { expires: 7 });
    },
  },
  mounted() {
    const wishlistFromCookie = Cookies.get("wishlist");
    if (wishlistFromCookie) {
      this.wishlist = JSON.parse(wishlistFromCookie);
    }
  },
};
</script>
<template>
  <div class="grid grid-flow-col">
    <div
      :class="{
        'grid justify-center items-center gap-4': true,
        'grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4':
          wishlist.length === 0,
        'grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-3':
          wishlist.length > 0,
      }"
    >
      <div v-for="(film, index) in films" :key="index">
        <div
          class="card border-solid hover:border-dotted border-y-cyan-900 border-2 flex flex-col justify-between grid-auto-rows gap-2 p-2 max-w-64"
        >
          <h2 class="bg-gray-200 mb-1">{{ film.title }}</h2>
          <img :key="film.picture" :src="film.picture" class="h-56" alt="" />
          <div class="flex flex-col gap-2">
            <p class="text-xs">{{ film.description }}</p>
            <div class="flex gap-2">
              <genre-tag v-for="genre in film.genre" :key="genre">{{
                genre
              }}</genre-tag>
            </div>
          </div>
          <button
            v-if="!isInWishlist(film)"
            class="rounded-md bg-green-200 hover:bg-green-300"
            @click="addToWishlist(film)"
          >
            Add to wishlist
          </button>
          <button
            v-if="isInWishlist(film)"
            class="rounded-md bg-red-200 hover:bg-red-300"
            @click="removeFromWishlist(film)"
          >
            Remove from Wishlist
          </button>
        </div>
      </div>
    </div>
    <div v-if="wishlist.length > 0" class="grid">
      <wish-list-component
        :wishlist="wishlist"
        @removeMovie="removeFromWishlist"
      ></wish-list-component>
    </div>
  </div>
</template>
<style scoped>
.card {
  min-height: 450px;
}
</style>
