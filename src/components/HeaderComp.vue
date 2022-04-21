<template>
    <div class="logoContainer d-flex justify-content-between align-items-center">
        <img class="logo" src="../../public/spotify-logo.png" alt="">
        <SelectComp @funzioneSelect="metodoSelect"/>
    </div>   
</template>

<script>
import SelectComp from './partials/SelectComp.vue'

export default{
    name: 'HeaderComp',
    components:{
        SelectComp
    },
    data(){
        return{
            testoSelect: ''
        }
        
    },
    methods: {
        metodoSelect(testo){
            this.testoSelect = testo;
        },
        filtraggio(){
            if (this.testoSelect === ''){
                //mostro lista completa
                return this.libraryArray;
            }
            return this.libraryArray.filter((elem) =>{
                return elem.genre.includes(this.testoSelect)
            });
        }
    },
}

</script>

<style scoped lang="scss">

.logoContainer{
    //height: 100px;
    background-color: #2D3A46;
}

.logo{
    width: 5%;
    padding: 10px 10px;
}

</style>
