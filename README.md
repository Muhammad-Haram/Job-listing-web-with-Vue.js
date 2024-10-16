<h1>Options Api vs Composition Api</h1>


<h1>Options Api</h1>

<script>
export default {
    data() {
        return {
            name: "Muhammad Haram",
            status: "active",
            tasks: ['1', '2', '3', '4', '5'],
            link: "https://github.com/"
        };
    },
    methods: {
        toggleStatus() {
            if (this.status === "active") {
                this.status = "pending";
            } else if (this.status === "pending") {
                this.status = "inactive";
            } else {
                this.status = "active";
            }
        },
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

    <a v-bind:href="link">github</a>
    <button @click="toggleStatus">click</button>

</template>


<h1>Composition Api</h1>

<script>
import { ref } from 'vue'

export default {
    setup() {
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

        return {
            name,
            status,
            tasks,
            toggleStatus
        }

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

