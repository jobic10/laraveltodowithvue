<template>
    <div class="addNote">
        <input type="text" v-model="note.name">
        <font-awesome-icon
        icon="plus-square"
        @click="addNote()"
        :class="[note.name ? 'active': 'inactive', 'plus']"
        />
    </div>
</template>
<script>
export default {
data: function(){
    return {
        note:{
            name: ""
        }
    }
},
methods: {
    addNote(){
        if(this.note.name == '')return;
        axios.post('api/note/store', {
            note: this.note
        }).then(
            response => {
                if (response.status == 201){
                    this.note.name = '';
                    alert("New Note Saved")
                }
            }
        ).catch(error => {
            alert(error)
        })
    }
}
}
</script>

<style scoped>
.addNote{
    display: flex;
    justify-content: center;
    align-items: center;
}

input{
    background: #f7f7f7;
    border: 0px;
    outline:none;
    padding:5px;
    margin-right: 10px;
    font-size: 30px;
    width: 100%;

}
.plus{
    font-size: 50px;
}
.active{
    color: #41912d;
}
.inactive{
    color: #999999;
}
</style>
