<template>
    <nav class="navbar navbar-light bg-danger">
        <div class="container-fluid">
            <a href="" class="navbar-brand text-white fs-2">Boolflix</a>
            <div class="d-flex">
                <input v-model="searchInput"
                class="form-control me-2" 
                type="search" 
                placeholder="Inserisci titolo..." 
                @keyup.enter="startNewSearch"
                >
                <button 
                @click="startNewSearch" 
                class="btn btn-outline-light" 
                type="submit">
                Cerca
                </button>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    name: 'IndexHeader',
    
    data: function(){
        return {
            searchInput : '',
        }
    },
    methods:{
        startNewSearch(){
            if (this.searchInput === ""){
                console.warn('non hai inserito niente.')
                
            } else {
            this.$emit('searchTitle', this.searchInput);
            }
        }
    }
}
</script>

<style lang="scss" scoped>

</style>

