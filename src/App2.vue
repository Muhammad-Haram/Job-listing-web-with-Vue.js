<!-- todo list code -->

<script setup>
import { ref, onMounted } from 'vue'


const name = ref("Muhammmad Haram");
const status = ref("active");
const tasks = ref(["task1", "task2", "task3"]);
const newTask = ref("")

const toggleStatus = () => {
    if (status.value === "active") {
        status.value = "pending";
    } else if (status.value === "pending") {
        status.value = "inactive";
    } else {
        status.value = "active";
    }
}

const addTask = () => {
    if (newTask.value.trim() !== "") {
        tasks.value.push(newTask.value);
        newTask.value = ""
    }
}

const deleteTask = (index) => {
    tasks.value.splice(index, 1);
}

onMounted(async () => {
    try {

        const res = await fetch("https://jsonplaceholder.typicode.com/todos")
        const data = await res.json();
        tasks.value = data.map((task) => (task.title))

    } catch (error) {
        console.log(error, "api fetch failed")
    }
})

</script>

<template>
    <h1>{{ name }}</h1>
    <p v-if="status === 'active'">User is Active</p>
    <p v-else-if="status === 'pending'">User is pending</p>
    <p v-else>User is not active</p>
    <h1>tasks</h1>
    <ul>
        <li v-for="(task, index) in tasks" :key='task'>
            <span>{{ task }}</span>
            <button @click="deleteTask(index)">x</button>
        </li>
    </ul>

    <button @click="toggleStatus">click</button>

    <form @submit.prevent="addTask">
        <label for="newTask"></label>
        <input type="text" id="newTask" name="newTask" v-model="newTask" />
        <button type="submit">Submit</button>
    </form>

</template>