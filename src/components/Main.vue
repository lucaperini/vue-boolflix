<template>
    <main>
        <div>
            <div class="text-center text-danger p-5"
                v-if="searchMoviesList.length <= 0 && searchSeriesList.length <= 0">
                <h5>Cerca un titolo...</h5>
            </div>
            <div v-else>
                <h2 v-if="searchMoviesList.length > 0">Film</h2>
                <section class="movie">
                    <Card 
                        v-for="item in searchMoviesList" 
                        :key="item.id" 
                        :result="item"
                    />
                </section>
                <h2 v-if="searchSeriesList.length > 0">Serie TV</h2>
                <section class="tv">
                    <Card 
                        v-for="item in searchSeriesList" 
                        :key="item.id" 
                        :result="item"
                    />
                </section>
            </div>
        </div>
    </main>
</template>

<script>
import Card from './Card.vue'
export default {
    name: 'IndexMain',
    components: {
    Card,
    },
    props: {
    searchMoviesList: Array,
    searchSeriesList: Array,
    }
}
</script>

<style>

</style>