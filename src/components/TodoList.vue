

<script setup>
//my task is to build a todo list in less than 20 minutes

import {ref} from 'vue'

const newTask= ref('')
const tasks = ref([])

const addTask = () => {
if(newTask.value.trim() != ''){
    tasks.value.push(newTask.value)
    newTask.value = ''
}
}

const removeTask = (index) => {
tasks.value.splice(index,1)
}
</script>

<template>
   
    <div class="todo">
        <h2>TODO LIST</h2>
        <input placeholder="enter a todo" @keyup.enter="addTask" v-model="newTask">
        <button @click="addTask">Add task</button>
        <ul>
            <li v-for="(task,index) in tasks" :key="index">
                {{ task }}
                <button class="btn2" @click="removeTask(index)"> Remove </button>
            </li>
        </ul>
    </div>
</template>

<style scoped>
.todo{
    border: 2px solid blue;
    padding: 50px;
    border-radius: 7px;
    margin: 0 auto;
    width:fit-content;
}

.btn2{
    background-color: red;
    color: white;
}
 h2{
    margin: 0 auto;
    /* margin-top: 20px; */
    width:fit-content;
 }

 li{
    margin-right: 30px;
 }

 button{
    background-color: green;
    color: white;
    border: none;
    padding: 4px;
    border-radius: 5px;
 }
</style>