<script setup>
import JobListings from "@/components/JobListings.vue";
</script>

<template>
    <JobListings v-bind:limit="Infinity" v-bind:showButton="false" />
</template>
