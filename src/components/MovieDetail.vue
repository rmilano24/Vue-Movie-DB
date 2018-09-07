<template>
    <transition name="fade">
        <div class="movie-wrapper" :style="styles">
            <div class="movie-info">
                <h1>{{ movie.title }}</h1>
                <h3>Release Date: {{ movie.release_date }}</h3>
                <p>{{ movie.overview }}</p>
            </div>
        </div>
    </transition>
</template>

<script>
    const BACKDROP_PATH = "http://image.tmdb.org/t/p/w1280";
    export default {
        data() {
            return {
                movie: {}
            }
        },
        beforeCreate() {
            console.log('before create')
        },
        created: function() {
            console.log('created')
            this.fetchData();
        },
        beforeMount() {
            console.log('before mount')
        },
        mounted() {
            console.log('mounted')
        },
        beforeUpdate() {
            console.log('before update')
        },
        update() {
            console.log('updated')
        },
        computed: {
            styles() {
                return {
                    background: `url(${BACKDROP_PATH}/${this.movie.backdrop_path}) no-repeat`
                }
            }
        },
        methods: {
            fetchData: async function() {
                try {
                   const res = await fetch(`https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=60ec72d3c6837c4e287d7292d3a025c2`);
                   const movie = await res.json();
                   this.movie = movie;
                } catch (e) {
                    console.log(e)
                }
            }
        },
    }
</script>

<style scoped>
    .movie-wrapper {
        position: relative;
        padding-top: 50vh;
        background-size: contain;
    }
    .movie-info {
        background: #fff;
        color: #222;
        padding: 2rem 10%;
    }
    .fade-enter-active, .fade-leave-active {
    transition: all 0.3s ease;
    }
    .fade-enter, .fade-leave-to {
        opacity: 0;
        transform: translateX(100%);
    }

</style>