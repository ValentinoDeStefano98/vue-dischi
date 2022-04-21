<template>
    <div class="row my-5" v-if="libraryArray.length == arrayLength">
        <div class="d-flex justify-content-around mb-5">
            <SelectComp @funzioneSelect="metodoSelect"/>
            <SelectAlbumComp @funzioneSelectAlbum="metodoSelectAlbum"/>
        </div>
        <CardLibrary
        v-for="(element, index) in arrayFilter()"
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
import SelectComp from './partials/SelectComp.vue'
import SelectAlbumComp from './partials/SelectAlbumComp.vue'

export default{
    name: 'LibraryComp',
    components: {
        CardLibrary,
        SelectComp,
        SelectAlbumComp
    },
    data(){
        return{
            libraryArray: [],
            arrayLength: null,
            testoSelect: '',
            testoAlbum: ''
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
    },
    methods: {
        metodoSelect(testo){
            this.testoSelect = testo
            console.log(this.testoSelect)
        },
        metodoSelectAlbum(album){
            this.testoAlbum = album
            console.log(this.testoAlbum)
        },
        arrayFilter(){
            if (this.testoSelect === "start" && this.testoAlbum === "start"){
                return this.libraryArray
            } else if (this.testoSelect != "start") {
                return this.libraryArray.filter((elem) => {
                    return elem.genre.toLowerCase().includes(this.testoSelect.toLowerCase())
                })
            } else if (this.testoAlbum != "start") {
                return this.libraryArray.filter((elem) => {
                    return elem.author.toLowerCase().includes(this.testoAlbum.toLowerCase())
                })
            }
        },
        /*
        arrayAlbumFilter(){
            if (this.testoAlbum === "start"){
                return this.libraryArray
            } else {
                return this.libraryArray.filter((elem) => {
                    return elem.author.toLowerCase().includes(this.testoAlbum.toLowerCase())
                })
            }
        }
        */
    }
}
</script>

<style scoped lang="scss">

</style>