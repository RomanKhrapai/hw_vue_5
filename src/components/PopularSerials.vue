<template>
    <GridFilms v-if="films" :films="films">

    </GridFilms>
</template>


<script>
import axiosInstance from "../services/axios.js"
import GridFilms from "./GridFilms.vue"
import CardFilm from "./CardFilm.vue"

export default {
    components: { GridFilms, CardFilm },

    data() {
        return {
            films: null
        }
    },
    methods: {
        getFilms() {
            axiosInstance.get('/discover/tv?include_adult=false&include_video=false&language=en-US&page=1&sort_by=popularity.desc').then(res => {

                this.films = res.data.results
            }).catch(error => {
                console.log(error)
            })
        },
    },
    mounted() {
        this.getFilms()
    }
}
</script>
  
<style scoped></style>