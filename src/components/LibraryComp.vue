<template>
    <div class="row">
        <CardLibrary
        v-for="(element, index) in libraryArray"
        :key="index"
        :poster="element.poster"
        :title="element.title"
        :author="element.author"
        :year="element.year"
        />
    </div>   
</template>

<script>
import axios from 'axios';
import CardLibrary from './partials/CardLibrary.vue'
export default{
    name: 'LibraryComp',
    components: {
        CardLibrary
    },
    data(){
        return{
            libraryArray: []
        }
    },
    created(){
        axios.get( 'https://flynn.boolean.careers/exercises/api/array/music' )
            .then((res)=>{
                console.log(res.data.response);
                this.libraryArray = res.data.response
            })
            .catch((error)=> {
                console.log(error)
            })
    }
}

</script>

<style scoped lang="scss">



</style>