<script setup>
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCards.vue";
import JobListings from "@/components/JobListings.vue";
</script>

<template>
    <!-- Props: Passing in Variable to a Vue Component.-->
    <Hero title="Become a Vue Dev" subtitle="Find the Vue job that fits your skills and needs" />
    <HomeCards />
    <JobListings v-bind:limit="3" v-bind:showButton="true" />
</template>
