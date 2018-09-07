<template>
   <ul>
       <li v-for="movie in movies">
           <Movie :movie="movie" />
       </li>
   </ul>
</template>

<script>
    import Movie from './Movie.vue';
    export default {
        name: 'MoviesList',
        data() {
            return {
                movies: []
            }
        },
        created: function() {
            this.fetchData();
        },
        methods: {
            fetchData: async function() {
                try {
                   const res = await fetch('https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=60ec72d3c6837c4e287d7292d3a025c2');
                   const movies = await res.json();
                   this.movies = movies.results;
                } catch (e) {
                    console.log(e)
                }
            }
        },
        components: {
            Movie
        }
    };
</script>

<style scoped>
    ul {
        display: grid;
        list-style: none;
        padding: 1rem;
        margin: 0;
        grid-row-gap: 1rem;
        grid-template-columns: repeat(6, 1fr)
    }

</style>