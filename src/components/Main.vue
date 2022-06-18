<template>
    <main>
        <div class="container">
           
            <div class="text-center text-white p-5 intro"
              v-if="searchMoviesList.length <= 0 && searchSeriesList.length <= 0">
                <h1><strong>Benvenuto in Boolflix!</strong></h1>
                <p>Cerca il tuo film o la tua serie tv preferita</p>
            </div>
            
            <div v-else class="row row-cols-4 text-center">
                <h2 class="text-white text-uppercase fw-bold p-4" v-if="searchMoviesList.length > 0">film</h2>
                <section class="col-12">
                    <Card 
                        v-for="item in searchMoviesList" 
                        :key="item.id" 
                        :result="item"
                        class="d-inline-block"
                    />
                </section>
                <h2 class="text-white text-uppercase fw-bold p-5" v-if="searchSeriesList.length > 0">serie tv</h2>
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
.intro{
   
   background-image: url(../assets/tv2.jpg);
   background-size: cover;
   width:auto;
   height:100vh;
   
}

</style>