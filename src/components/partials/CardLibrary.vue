<template>
    <div class="col-3 text-center my-5 posterContainer">
        <img :src="poster" alt="copertina canzone" class="poster">
        <h3>{{title}}</h3>
        <h5>{{author}}</h5>
        <h5>{{year}}</h5>
    </div>   
</template>

<script>

export default{
    name: 'CardLibrary',
    props:{
        poster: String,
        title: String,
        author: String,
        genre: String,
        year: String,
    }
}

</script>

<style scoped lang="scss">

.posterContainer{
    border: 1px solid black;
    padding: 15px 0;
}

.poster{
    max-width: 80%;
}
</style>