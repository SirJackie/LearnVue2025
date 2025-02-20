<script>
export default {
    data() {
        return {
            name: "SirJackie",
            status: "active",
            tasks: ["Task 1", "Task 2", "Task 3"],
            links: "https://www.microsoft.com/"
        }
    },
    methods: {
        callback(){
            console.log("Callback Triggered!");
        },
        toggleStatus() {
            if (this.status === "active"){
                this.status = "pending";
            }
            else if (this.status === "pending") {
                this.status = "inactive";
            }
            else {
                this.status = "active";
            }
        }
    }
}
</script>

<template>
    <!-- Heading -->
    <h1>{{ name }} ({{ status }})</h1>
    <p v-if="status === 'active'">User is active!</p>
    <p v-else-if="status == 'pending'">User is pending!</p>
    <p v-else>User is inactive!</p>
    <button v-on:click="toggleStatus()">Toggle Status</button>

    <!-- Task List -->
    <h2 style="margin-top: 2vh;">Tasks:</h2>
    <ul>
        <li v-for="task in tasks" v-bind:key="task">{{ task }}</li>
    </ul>

    <!-- Some Links For Testing -->
    <h2 style="margin-top: 2vh;">Link VBind Test:</h2>
    <a v-bind:href="links">Access Binded Link</a><br>
    <button v-on:click="console.log('VOn Triggered!');">Click Me!</button><br>
    <button v-on:click="callback()">Callback.</button><br>

</template>
