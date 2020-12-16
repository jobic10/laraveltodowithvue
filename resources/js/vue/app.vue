<template>
    <div class="todoListContainer">
       <div class="heading">
       <h2 class="title">Todo list</h2>
        <add-note-form v-on:reloadList="getNote()"/>
        <list-view :notes='notes'
        v-on:reloadlist="getNote()"
        />
       </div>
    </div>
</template>
<script>
import AddNoteForm from './addNoteForm'
import ListView from './listView.vue'

export default {
components: {
    AddNoteForm,
    ListView,

},
data: function(){
    return {
        notes: []
    }
},
methods: {
    getNote(){
        axios.get('api/notes')
        .then(response => {
            this.notes = response.data
        })
        .catch(error => alert(error));
    }
},
created(){
    this.getNote();
}
}
</script>

<style scoped>
    .todoListContainer{
        width: 350px;
        margin: auto;
    }
    .heading{
        background: #e6e6e6;
        padding: 10px
    }
    #title{
        text-align: center ;
    }
</style>
