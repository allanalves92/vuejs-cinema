<template>
    <div id="detail" v-if="movie">
        <movie-item class="movie" :movie="movie">
            <div class="movie-details">
                <p class="movie-genre">{{movie.genre}}</p>
                <p class="movie-plot">{{movie.Plot}}</p>
            </div>
            <table>
                <tr>
                    <td>Release date:</td>
                    <td>{{movie.Released}}</td>
                </tr>
                <tr>
                    <td>Running time:</td>
                    <td>{{movie.Runtime}}</td>
                </tr>
                <tr>
                    <td>Director:</td>
                    <td>{{movie.Director}}</td>
                </tr>
                <tr>
                    <td>Cast:</td>
                    <td>{{movie.Actors}}</td>
                </tr>
            </table>
        </movie-item>
        <div class="home">
            <router-link :to="{name: 'home'}">Back to results</router-link>
        </div>
    </div>
</template>

<script>
import MovieItem from "./MovieItem.vue";
export default {
  props: ["movies"],
  components: {
    MovieItem
  },
  computed: {
    movie() {
      let movie = this.movies.find(movie => movie.id == this.$route.params.id);
      return movie ? movie.movie : null;
    }
  },
  created() {}
};
</script>