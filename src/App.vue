<script setup>
import { ref } from 'vue'


const name = ref("Muhammmad Haram");
const status = ref("active");
const tasks = ref(["task1", "task2", "task3"]);

const toggleStatus = () => {
    if (status.value === "active") {
        status.value = "pending";
    } else if (status.value === "pending") {
        status.value = "inactive";
    } else {
        status.value = "active";
    }
}
</script>

<template>
    <h1>{{ name }}</h1>
    <p v-if="status === 'active'">User is Active</p>
    <p v-else-if="status === 'pending'">User is pending</p>
    <p v-else>User is not active</p>
    <h1>tasks</h1>
    <ul>
        <li v-for="task in tasks" :key='task'>{{ task }}</li>
    </ul>

    <button @click="toggleStatus">click</button>

</template>