<template>
    <div class="todoListContainer">
       <div class="heading">
       <h2 class="title">Todo list</h2>
        <add-note-form />
        <!-- <list-view /> -->
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
