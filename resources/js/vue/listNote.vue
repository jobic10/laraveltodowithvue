<template>
    <div class="note">
        <input
        type="checkbox"
        @change='updateCheck()'
        v-model='note.completed'
        />
        <span :class="[note.completed ? 'completed' : '', 'noteText']"> {{ note.name }} </span>
        <button @click='removeNote()' class="trashcan" >
        <font-awesome-icon icon='trash' />
        </button>
    </div>
</template>
<script>
export default {
props: ['note'],
methods:{
    updateCheck(){
        axios.put('api/note/'+ this.note.id, {note: this.note}).
        then(response => {
            if (response.status == 200){
                this.$emit('notechanged');
            }
        }).
        catch(error => {
            alert(error)
        });
    },
    removeNote(){
        if (confirm('Are you sure about this?')){
             axios.delete('api/note/' + this.note.id).
        then(response => {
            if (response.status == 200){
                this.$emit('notechanged');
            }
        }).
        catch(error => {
            alert(error)
        });
        }

    }
}
}
</script>


<style scoped>
    .completed{
        text-decoration: line-through;
        color: #999999;
    }
    .noteText{
        width: 100%;
        margin-left: 20px;
    }
    .note{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .trashcan{
        background: #e6e6e6;
        border: none;
        color: #ff0000;
        outline: none;
    }
</style>
