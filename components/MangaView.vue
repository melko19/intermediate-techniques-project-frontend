<template>
    <div>
        <button class="btn btn-success float-right" @click="onNew">
            Add Manga
        </button>
        <h5>Manga Entry</h5>
        
        <hr>

        <form action="#" @submit.prevent="onSave">
            
            <b-form-group   label="Title">
                <b-form-input v-model="manga.title"></b-form-input>
            </b-form-group>

            <b-form-group   label="Author">
                <b-form-input v-model="manga.author"></b-form-input>
            </b-form-group>

            <b-form-group   label="Publisher">
                <b-form-input v-model="manga.publisher"></b-form-input>
            </b-form-group>

            <b-form-group   label="Genre">
                <b-form-input v-model="manga.genre"></b-form-input>
            </b-form-group>

            <b-form-group   label="Price">
                <b-form-input v-model="manga.price"></b-form-input>
            </b-form-group>

            <b-form-group   label="Date Aquired">
                <b-form-input type="date" v-model="manga.acquired_on"></b-form-input>
            </b-form-group>

            <b-form-group>
                <button class="btn btn-primary" type="submit">Save Changes</button>
                <button class="btn btn-danger" type="button" @click="onDelete" v-if="manga.id">Delete</button>
            </b-form-group>

        </form>
    </div>
</template>

<script>
export default {
    props: {
        manga:{}
    },
    methods: {
        async onSave(){
            try{
                if(!this.manga.id){
                    await this.$axios.post('http://localhost:8000/api/mangas', this.manga)
                }else{
                    await this.$axios.put('http://localhost:8000/api/mangas/' + this.manga.id, this.manga)
                }

                this.$emit('saved');
            }catch(err){
                alert(err.response.data.message)
            }  
        },

        onNew() {
            this.$emit('newManga')
        },

        async onDelete() {
            try {
                this.$axios.delete('http://localhost:8000/api/mangas/' + this.manga.id)

                this.$emit('deleted')
                
            } catch (error) {
                alert(error.response.data.message)
            }
            
        }
    }
}
</script>
<style scoped>

</style>