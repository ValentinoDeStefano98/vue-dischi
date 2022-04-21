<template>
    <div class="row my-5" v-if="libraryArray.length == arrayLength">
        <CardLibrary
        v-for="(element, index) in libraryArray"
        :key="index"
        :poster="element.poster"
        :title="element.title"
        :author="element.author"
        :year="element.year"
        />
    </div>
    <div v-else>
        <img src="./../../public/480px-Loader.gif" alt="">
    </div>
</template>

<script>
import axios from 'axios';
import CardLibrary from './partials/CardLibrary.vue'

export default{
    name: 'LibraryComp',
    components: {
        CardLibrary,
        
    },
    data(){
        return{
            libraryArray: [],
            arrayLength: null,
        }
    },
    created(){
        axios.get( 'https://flynn.boolean.careers/exercises/api/array/music' )
            .then((res)=>{
                this.libraryArray = res.data.response
                this.arrayLength = res.data.response.length
                console.log(this.arrayLength)
            })
            .catch((error)=> {
                console.log(error)
            })
    }
}

</script>

<style scoped lang="scss">

</style>