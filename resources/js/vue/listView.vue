<template>
<div class="div">
    <div v-for="(note, index) in notes" :key="index">
        <list-note
        :note='note'
        class="note"
        v-on:notechanged="$emit('reloadlist')" />
    </div>
</div>
</template>
<script>
import listNote from './listNote'
import ListNote from './listNote.vue'
export default {
    props: ['notes'],
    components: {
        listNote
    }
}
</script>

<style scoped>
    .note{
        background: #e6e6e6;
        padding: 5px;
        margin-top: 5px;
    }
</style>
