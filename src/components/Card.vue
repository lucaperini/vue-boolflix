<template>
    <div>
        <!-- Poster Film -->
        <div v-if="result.title">
          <img v-if="result.poster_path !== null" 
            
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" 
            :alt="`Poster ${result.title}`"
          >
          <h2 v-else>{{result.title}} <p>Nessuna immagine disponibile</p> </h2>
        </div>

        <!-- Poster serie tv -->
        <div v-else>
          <img v-if="result.poster_path !== null"
            class="poster" 
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" 
            :alt="`Poster ${result.name}`"
          >
          <h2 v-else>{{result.name}} <p>Nessuna immagine disponibile</p> </h2>
        </div>
        <ul>
            <li>
                <h4 class="fw-bold">Titolo: </h4>
                <p v-if="result.title">
                {{result.title}}
                </p>
                <p v-else>{{result.name}}</p>
            </li>
            <li>
                <h4 class="fw-bold">Titolo originale: </h4>
                <p v-if="result.original_title">
                {{result.original_title}}</p>
                <p v-else>{{result.original_name}}</p>
            </li>
            <li>
                <h4 class="fw-bold">Lingua originale: </h4>
                <lang-flag v-if="result.original_language !== null" :iso="result.original_language" title="country flag" />
                <p v-else>{{result.original_language}} non disponibile</p>
                  
            </li>
            <li>
                <h4 class="fw-bold">Voto: </h4>
                <p>{{Math.ceil(result.vote_average)}}</p>
            </li>
            <li>
            <h4 class="fw-bold">Valutazione: </h4>
                <i v-for="index in starsNumber(result)" :key="index" 
                class="fas fa-star text-warning"></i>
                <i v-for="index in (maxStars - starsNumber(result))" :key="index" 
                class="far fa-star text-warning"></i>
            </li>
        </ul>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: 'IndexCard',

  props: {
    result: Object
  },

  components: {
    LangFlag,
  },

  data(){
    return {
      maxStars: 5
    }
  },
  methods:{
    starsNumber(result){
      return Math.ceil(result.vote_average / 2)
    },
  }
}
</script>

<style lang="scss">
</style>
