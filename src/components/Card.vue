<template>
 <div class="flip-card">
  <div class="flip-card-inner">
    <div class="flip-card-front">
      
      <div v-if="result.title">
          <img v-if="result.poster_path !== null" 
            
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" 
            :alt="`Poster ${result.title}`"
          >
          <p class="fw-bold px-2" v-else>immagine non disponibile</p>
        </div>

        <!-- Poster serie tv -->
        <div v-else >
          <img v-if="result.poster_path !== null"
            class="poster" 
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" 
            :alt="`Poster ${result.name}`"
          >
          <p class="fw-bold px-2" v-else>immagine non disponibile </p>
        </div>
    </div>
    <div class="flip-card-back">
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
  </div>





    
    
        
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

<style lang="scss" scoped>

ul > li{
  list-style-type: none;
}

.flip-card {
  background-color: transparent;
  width: 300px;
  height:400px;
  border: 1px solid #f1f1f1;
  perspective: 1000px
}
.flip-card-inner img{
  width:100%;
  height:100%;
  object-fit:contain;
  object-position:center top;

}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}


.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}


.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}


.flip-card-front {
  background-color: #bbb;
  color: black;
}


.flip-card-back {
  background-color: dodgerblue;
  color: white;
  transform: rotateY(180deg);
} 


</style>
