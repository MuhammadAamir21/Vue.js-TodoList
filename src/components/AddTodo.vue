<template>
    <div>
        <!-- .stop.prevent prevent it from reloading the page -->
        <form @submit="addTodo">
        <input type="text" v-model="title" name="title" placeholder="Add Todo...">
        <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>
<script>
//import uuid from 'uuid';
import { v4 as uuidv4 } from 'uuid';

export default {
    name:"AddTodo",
    data() {
        return {
            title:''
        }
    },
    methods: {
        addTodo(e){
            //Work same as
            //.stop.prevent prevent it from reloading the page
            e.preventDefault();
            
            const newTodo ={
                //npm i uuid
                //A simple unique id generator
                id: uuidv4(),
                title: this.title,
                completed: false
            }
            //Send up to parent
            this.$emit('add-todo',newTodo);
            this.title='';
        }
    },
}
</script>
<style scoped>
form{
    display: flex;
}
input[type="text"]{
    flex: 10;
    padding: 5px;
}
input[type="submit"]{
    flex: 2;
}
</style>