<script>
export default {
    data() {
        return {
            name: "Muhammad Haram",
            status: "active",
            tasks: ['1', '2', '3', '4', '5'],
            link : "https://github.com/"
        }
    },
}
</script>

<template>
    <h1>{{ name }}</h1>
    <p v-if="status === 'active'">User is Active</p>
    <p v-else-if="status === 'pending'">User is pending</p>
    <p v-else>User is not active</p>
    <h1>tasks</h1>
    <ul>
        <li v-for="task in tasks" :key = 'task'>{{ task }}</li>
    </ul>

    <a v-bind:href="link">github</a>

</template>