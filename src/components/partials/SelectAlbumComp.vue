<template>
    <div>
        <select class="form-select" aria-label="Default select example" v-model="selectedAlbum" @change="$emit('funzioneSelectAlbum', selectedAlbum)">
            <option value="" disabled selected>Seleziona l'artista</option>
            <option value="start">-</option>
            <option value="BonJovi">Bon Jovi</option>
            <option value="Queen">Queen</option>
            <option value="Sting">Sting</option>
            <option value="SteveGaddBand">Steve Gadd Band</option>
            <option value="IronMaided">Iron Maiden</option>
            <option value="EricClapton">Eric Clapton</option>
            <option value="DeepPurple">Deep Purple</option>
            <option value="Metallica">Metallica</option>
            <option value="DaveWeckl">Dave Weckl</option>
            <option value="MichaelJacjson">Michael Jackson</option>
        </select>
    </div>   
</template>

<script>

export default{
    name: 'SelectAlbumComp',
    data(){
        return{
            selectedAlbum: ''
        }
    }
}

</script>

<style scoped lang="scss">

</style>