<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <div v-if="result.title">
          <img
            v-if="result.poster_path !== null"
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`"
            :alt="`Poster ${result.title}`"
          />

          <div class="lh-1" v-else>
            <img class="p-1" src="../assets/placeimg.jpg" />

            <p class="fw-bold px-2 text-warning text-center border-warning">
              {{ result.title }}
            </p>

            <p class="text-center">immagine non disponibile</p>
          </div>
        </div>
        <div v-else>
          <img
            v-if="result.poster_path !== null"
            class="poster"
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`"
            :alt="`Poster ${result.name}`"
          />
          <div class="lh-1" v-else>
            <img class="p-1" src="../assets/placeimg.jpg" />

            <p class="fw-bold px-2 text-warning text-center border-warning">
              {{ result.name }}
            </p>

            <p class="text-center">immagine non disponibile</p>
          </div>
        </div>
      </div>
      <div class="flip-card-back overflow-auto">
        <ul>
          <li>
            <p class="fw-bold d-inline-block">Titolo:</p>
            <p v-if="result.title">
              {{ result.title }}
            </p>
            <p v-else>{{ result.name }}</p>
          </li>
          <li>
            <p class="fw-bold">Titolo originale:</p>
            <p v-if="result.original_title">
              {{ result.original_title }}
            </p>
            <p v-else>{{ result.original_name }}</p>
          </li>
          <li>
            <p class="fw-bold">Lingua originale:</p>
            <lang-flag
              class="mx-2"
              v-if="result.original_language"
              :iso="result.original_language"
              title="country flag"
            />
            <p v-else>{{ result.original_language }}</p>
          </li>
          <!-- <li>
                <h4 class="fw-bold">Voto: </h4>
                <p>{{Math.ceil(result.vote_average)}}</p>
            </li> -->
          <li>
            <p class="fw-bold">Valutazione:</p>
            <i
              v-for="index in starsNumber(result)"
              :key="index"
              class="fas fa-star text-warning"
            ></i>
            <i
              v-for="index in maxStars - starsNumber(result)"
              :key="index"
              class="far fa-star text-warning"
            ></i>
          </li>
          <li>
            <p class="fw-bold">Descrizione:</p>
            <p v-if="result.overview !== ''">
              {{ result.overview }}
            </p>
            <p v-else>non disponibile</p>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";

export default {
  name: "IndexCard",

  props: {
    result: Object,
  },

  components: {
    LangFlag,
  },

  data() {
    return {
      maxStars: 5,
    };
  },
  methods: {
    starsNumber(result) {
      return Math.ceil(result.vote_average / 2);
    },
  },
};
</script>

<style lang="scss" scoped>



ul {
  padding: 1rem;
}

ul > li {
  list-style-type: none;
  margin-top: 0;
  line-height: 1rem;
}

ul > li p {
  display: inline-block;
  padding: 0 0.2rem;
  line-height: 1rem;
  color: white;
}

.flip-card {
  background-color: transparent;
  width: 300px;
  height: 400px;
  perspective: 1000px;
  margin-bottom: 2rem;
}

.flip-card-front img {
  width: 100%;
  height: 100%;
  object-fit: cover;

  border-radius: 1.5rem;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: left;
  transition: transform 0.8s;
  transform-style: preserve-3d;
  display: inline-block;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
  cursor: pointer;
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  padding: 1.2rem;
}

.flip-card-front {
  background-color: transparent;
  color: white;
}

.flip-card-back {
  background-color: rgb(26, 53, 73);
  color: white;
  margin-top: 1rem;
  transform: rotateY(180deg);
  line-height: 0.8rem;
  font-size: 0.8rem;
  border-radius: 1.5rem;
  border: 3px solid goldenrod;
  align-items: center;
  z-index: 10;
}
</style>
