<template>
    <div class="bgd">
        <Navbar />
        <div class="container">
            <br>
            <h1>Manga Collection</h1>
            <div class="row">
                <div class="col-6">
                    <h5>List of Manga</h5>
                    <ul class="list-group">
                        <li class="list-group-item list-group-item-action" v-for="manga in mangas" :key="manga.id" @click="onSelected(manga)">
                            {{manga.title}} <span class="float-right">{{manga.genre}}</span>
                        </li>
                    </ul>
                </div>

                <div class="col-6">
                    <MangaView :manga="selectedManga" @saved="onSave" @newManga="onNew" @deleted="onDelete"/>
                </div>
            </div>
        </div>

    </div>
</template>
<script>
export default {
    data(){
        return{
            mangas: [],
            selectedManga:{}
        }
    },
    methods: {
        async getAll(){
            await this.$axios.get('http://localhost:8000/api/mangas')
            .then((res)=>{
                if(res.status=200){
                    this.mangas = res.data
                    console.log(this.mangas)
                }
            })
        },
        onSave(){
            this.getAll()
            this.selectedManga
        },
        onSelected(manga){
            this.selectedManga = manga
        },
        onNew() {
            this.selectedManga = {}
        },
        onDelete() {
            this.getAll()
        }
    },
    created(){
        this.getAll()
        this.selectedManga = {}
    }
}
</script>
<style scoped>

    .bgd{
      background-color: #0b5f94;
      height: 765px;
    }

</style>