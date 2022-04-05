<template>
    <main>
        <div class="container-fluid">
            <div class="text-center text-danger p-5"
                v-if="searchMoviesList.length <= 0 && searchSeriesList.length <= 0">
                <h5>Cerca un titolo...</h5>
            </div>
            <div v-else class="d-flex row row-cols-5">
                <h2 v-if="searchMoviesList.length > 0"></h2>
                <section class="movie col-12">
                    <Card 
                        v-for="item in searchMoviesList" 
                        :key="item.id" 
                        :result="item"
                        class="d-inline-block"
                    />
                </section>
                <h2 v-if="searchSeriesList.length > 0"></h2>
                <section class="tv col-12">
                    <Card 
                        v-for="item in searchSeriesList" 
                        :key="item.id" 
                        :result="item"
                        class="d-inline-block"
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

<style lang="scss" scoped>


</style>