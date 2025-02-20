<script setup>
import { ref, onMounted } from "vue";
import tasksJson from "@/assets/todos.json";

const name = ref("SirJackie");
const status = ref("active");
const tasks = ref(["Task 1", "Task 2", "Task 3"]);
const newTask = ref("");

const toggleStatus = () => {
    if (status.value === "active"){
        status.value = "pending";
    }
    else if (status.value === "pending"){
        status.value = "inactive";
    }
    else{
        status.value = "active";
    }
};

const addTask = () => {
    if (newTask.value.trim() !== ""){
        tasks.value.push(newTask.value);
    }
}

const deleteTask = (index) => {
    tasks.value.splice(index, 1);
};

onMounted(async () => {
    try {
        // const response = await fetch("https://jsonplaceholder.typicode.com/todos");
        // const data = await response.json();
        const data = tasksJson;
        tasks.value = data.map((task) => task.title);
    } catch (error) {
        console.log("Error fetching tasks: ", error);
    }
});
</script>

<template>
    <!-- User Info -->
    <h1>{{ name }} ({{ status }})</h1>
    <button v-on:click="toggleStatus()">
        Toggle Status
    </button>

    <!-- Task List -->
    <h2 style="margin-top: 2vh;">Tasks:</h2>
    <ul>
        <li v-for="(task, index) in tasks" v-bind:key="task">
            {{ task }}
            <button v-on:click="deleteTask(index)">x</button>
        </li>
    </ul>

    <!-- Form for Submit -->
    <h2 style="margin-top: 2vh;">Form:</h2>
    <form v-on:submit.prevent="addTask()">
        <label for="newTask">Add Task: </label>
        <input type="text" id="newTask" name="newTask" v-model="newTask">&nbsp;
        <button type="Submit">Submit</button>
    </form>
</template>
