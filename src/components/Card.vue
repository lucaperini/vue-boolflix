<template>
    <div>
        <ul>
            <li>
                <h3 class="fw-bold">Titolo: </h3>
                <p v-if="result.title">
                {{result.title}}
                </p>
                <p v-else>{{result.name}}</p>
            </li>
            <li>
                <h3 class="fw-bold">Titolo originale: </h3>
                <p v-if="result.original_title">
                {{result.original_title}}</p>
                <p v-else>{{result.original_name}}</p>
            </li>
            <li>
                <h3 class="fw-bold">Lingua originale: </h3>
                <img class="language-flag" 
                src="../assets/logo.png" alt="italian flag"
                v-if="result.original_language == 'it'">
                <img class="language-flag" 
                src="../assets/logo.png" alt="uk flag"
                v-else-if="result.original_language == 'en'">
                <p v-else>{{result.original_language}}</p>
            </li>
            <li>
                <h3 class="fw-bold">Titolo: </h3>
                <p>{{result.vote_average}}</p>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    
    name: 'IndexCard',
    
    props: {
    result: Object,
    },
}
</script>

<style lang="scss">
</style>
