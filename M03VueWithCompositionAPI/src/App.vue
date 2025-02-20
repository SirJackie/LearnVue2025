<script setup>
import { ref } from "vue";

const name = ref("SirJackie");
const status = ref("active");
const tasks = ref(["Task 1", "Task 2", "Task 3"]);

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
</script>

<template>
    <h1>{{ name }} ({{ status }})</h1>
    <button v-on:click="toggleStatus()">
        Toggle Status
    </button>

    <h2 style="margin-top: 2vh;">Tasks:</h2>
    <ul>
        <li v-for="task in tasks" v-bind:key="task">
            {{ task }}
        </li>
    </ul>
</template>
